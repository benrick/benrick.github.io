---
layout: post
title: "Beginning Unit Testing"
date: 2008-11-26 22:21:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Beginning-Unit-Testing/"
---
<!-- more -->

<p>Getting started unit testing is a difficult task. I've seen plenty of people learning to unit test and it took some time for me and seems to take some time for everyone before unit testing really clicks. Part of the reason why unit testing is difficult for people to get started with is that the code most developers write is not testable. Yes, not only is it important to test, but it is important for your code to be testable. Most code is so difficult to test that anyone who doesn't know how to unit test will have a great deal of trouble testing anything.</p>
<p>Most testing is difficult because the code you're trying to test has too many dependencies. So we all know that we write code which depends on other code we write. There are a few important dependencies that a lot of people forget about.</p>
<h3>Breaking the DateTime Dependency</h3>
<p>One seemingly safe piece of code to test is the DateTime class. How is it often used? Well, people use DateTime.Now or DateTime.Today in their code. So what is the big deal? Isn't this easy to test? NO! Testing a method which uses either of those two values is not easy at all. If your application cares about the time of day at all, it is impossible to test it reliably if you're using DateTime.Now.</p>
<p>Two cases for time come into my mind right now: checking for weekends and checking morning, afternoon, and evening. A couple of interesting sites I enjoy change the theme of the site based on the time of day. How could you test that logic? Well, not easily if you're using DateTime directly. To get around this wee need to break the dependency. To do this we need to work with an interface which gives us access to all the logic we used from the DateTime class.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color: #0000ff">interface</span> ICalendar
{
    DateTime GetCurrentTime();
    DateTime GetCurrentDate();
}

<span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> Calendar : ICalendar
{
    <span style="color: #cc6633">#region</span> ICalendar Members

    <span style="color: #0000ff">public</span> DateTime GetCurrentTime()
    {
        <span style="color: #0000ff">return</span> DateTime.Now;
    }

    <span style="color: #0000ff">public</span> DateTime GetCurrentDate()
    {
        <span style="color: #0000ff">return</span> DateTime.Today;
    }

    <span style="color: #cc6633">#endregion</span>
}</pre>
</div>
<p>If you need any more attributes from the DateTime class add the methods for them to the interface and the class.</p>
<p>In order to use these methods in production with our TimeOfDay class, we will need to do a couple of things. As a general rule, it is important to program against an interface. We will start by creating a stub for the class and then testing the stub.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> TimeOfDay
{
    <span style="color: #0000ff">private</span> ICalendar _calendar;
    <span style="color: #0000ff">public</span> TimeOfDay() : <span style="color: #0000ff">this</span>(<span style="color: #0000ff">new</span> Calendar())
    {
    }

    <span style="color: #0000ff">public</span> TimeOfDay(ICalendar calendar)
    {
        _calendar = calendar;
    }

    <span style="color: #0000ff">public</span> <span style="color: #0000ff">bool</span> IsMorning()
    {
        <span style="color: #0000ff">throw</span> <span style="color: #0000ff">new</span> NotImplementedException();
    }

    <span style="color: #0000ff">public</span> <span style="color: #0000ff">bool</span> IsEvening()
    {
        <span style="color: #0000ff">throw</span> <span style="color: #0000ff">new</span> NotImplementedException();
    }
}</pre>
</div>
<p>Now we go and write a couple of test methods which we want to have fail since we haven't implemented our methods yet. Then once we've got the tests in place we can fill in the code and have confirmation that we have written it correctly.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;">[TestClass]
<span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> TimeOfDayTester
{
    <span style="color: #0000ff">private</span> FakeCalendar _myFakeCalendar;

    <span style="color: #0000ff">public</span> TimeOfDayTester()
    {
        _myFakeCalendar = <span style="color: #0000ff">new</span> FakeCalendar();
    }

    [TestMethod]
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">void</span> OneMinuteBeforeTenAMShouldBeTheMorning()
    {
        _myFakeCalendar.CurrentTime = <span style="color: #0000ff">new</span> DateTime(2001, 1, 1, 9, 59, 00);
        TimeOfDay timeOfDay = <span style="color: #0000ff">new</span> TimeOfDay(_myFakeCalendar);
        Assert.IsTrue(timeOfDay.IsMorning());
    }

    [TestMethod]
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">void</span> NoonShouldNotBeTheMorning()
    {
        _myFakeCalendar.CurrentTime = <span style="color: #0000ff">new</span> DateTime(2001, 1, 1, 12, 00, 00);
        TimeOfDay timeOfDay = <span style="color: #0000ff">new</span> TimeOfDay(_myFakeCalendar);
        Assert.IsFalse(timeOfDay.IsMorning());
    }

    [TestMethod]
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">void</span> EightPMShouldNotBeTheMorning()
    {
        _myFakeCalendar.CurrentTime = <span style="color: #0000ff">new</span> DateTime(2001, 1, 1, 20, 00, 00);
        TimeOfDay timeOfDay = <span style="color: #0000ff">new</span> TimeOfDay(_myFakeCalendar);
        Assert.IsFalse(timeOfDay.IsMorning());
    }

    [TestMethod]
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">void</span> SixPMShouldBeTheEvening()
    {
        _myFakeCalendar.CurrentTime = <span style="color: #0000ff">new</span> DateTime(2001, 1, 1, 18, 00, 00);
        TimeOfDay timeOfDay = <span style="color: #0000ff">new</span> TimeOfDay(_myFakeCalendar);
        Assert.IsTrue(timeOfDay.IsEvening());
    }

    [TestMethod]
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">void</span> NoonShouldNotBeTheEvening()
    {
        _myFakeCalendar.CurrentTime = <span style="color: #0000ff">new</span> DateTime(2001, 1, 1, 12, 00, 00);
        TimeOfDay timeOfDay = <span style="color: #0000ff">new</span> TimeOfDay(_myFakeCalendar);
        Assert.IsFalse(timeOfDay.IsEvening());
    }

    [TestMethod]
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">void</span> EightAMShouldNotBeTheEvening()
    {
        _myFakeCalendar.CurrentTime = <span style="color: #0000ff">new</span> DateTime(2001, 1, 1, 8, 00, 00);
        TimeOfDay timeOfDay = <span style="color: #0000ff">new</span> TimeOfDay(_myFakeCalendar);
        Assert.IsFalse(timeOfDay.IsEvening());
    }
}
</pre>
</div>
<p>Now we can execute the tests and see them fail. This confirms that we haven't made any bad assumptions.</p>
<p><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/BeginningUnitTesting_12A30/NotImplementedTestFailures_3.jpg" border="0" alt="NotImplementedTestFailures" width="361" height="166" /></p>
<p>Now we go and write the code which makes the tests pass. Once the tests pass we know that the code works.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> TimeOfDay
{
    <span style="color: #0000ff">private</span> ICalendar _calendar;
    <span style="color: #0000ff">public</span> TimeOfDay() : <span style="color: #0000ff">this</span>(<span style="color: #0000ff">new</span> Calendar())
    {
    }

    <span style="color: #0000ff">public</span> TimeOfDay(ICalendar calendar)
    {
        _calendar = calendar;
    }

    <span style="color: #0000ff">public</span> <span style="color: #0000ff">bool</span> IsMorning()
    {
        <span style="color: #0000ff">return</span> (_calendar.GetCurrentTime().Hour &lt; 10);
    }

    <span style="color: #0000ff">public</span> <span style="color: #0000ff">bool</span> IsEvening()
    {
        <span style="color: #0000ff">return</span> (_calendar.GetCurrentTime().Hour &gt;= 18);
    }
}</pre>
</div>
<p>So now when we run our tests again we should see all green passing tests.</p>
<p><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/BeginningUnitTesting_12A30/PassingTests_3.jpg" border="0" alt="PassingTests" width="552" height="175" /></p>
<p>If we hadn't kept the DateTime class at arms length we wouldn't have been able to easily test the class. The reason we can't is because we are not able to set the value which will be returned from DateTime.Now. Anytime you use classes which magically give you access to something, they better have an interface. If they do not have an interface then you will need to use a solution like this one to wrap the class inside of another one.</p>
