[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/automated-ui-testing/1.png

### ABOUT AUTOMATED UI TESTING

![1]

User Interface test automation is a tricky practice. UI tests are an essential part of protecting your application's critical paths, and it's easy to start building them in the wrong way.

**Graphical user interface testing** is a testing framework that generates user interface events such as keystrokes and mouse clicks, and observes the changes that result in the user interface, to validate that the observable behavior of the program is correct. You are lucky! Zebble framework has a fantastic feature for UI testing. You can add the NuGet package of Zebble.UITesting to your solution.

#### UI Automation: Before You Even Start

Welcome to the first of two articles on being successful with user interface (UI) automation. The goal of these articles is to help you start asking the right questions to begin building high-value, maintainable automation in place for your projects. Once you’re past the basics, we hope to help you find the right questions on how to evolve your testing over time to continue adding value to your project.

You’ll notice we have mentioned “questions” a lot; answers, not so much. UI automation is a difficult domain to work in, and there aren’t any magic “best practices” other than one: use your brain. This short series will hopefully give you some ideas on how to look at your specific environment, and how to create a new (or tailor an existing!) automation strategy.

#### Why do UI Automation in the First Place?

Your first question about UI automation is one that’s too often missed: why do UI automation at all? Aren’t unit, integration, and manual/exploratory tests enough?

We in the software industry don’t ask “Why?” anywhere near as often as we should. UI automation is a significant cost in your overall development cycle. It’s important you understand if it’s worth the cost before jumping in!

UI automation ensures you’ve got tripwires around your most critical business value features in your system. Hopefully you’ve got a solid amount of test automation at other levels, but while unit and integration tests are critical to a system’s overall automation approach, by definition they don’t cross all boundaries of a functional slice.

Teams should **not** look to UI automation as a replacement for the thousands manual test scripts they have in place. That is a painful path that’s guaranteed to lead to failure. Those manual scripts should be evaluated to understand what critical “Show me the money!” features and use cases they’re guarding.

#### Goals for Automation

It’s a perfectly valid question, and one your team needs to answer. As part of answering that question, get distinct goals in mind for your automation effort, such as (for example):

- Increasing communication about testing across your team
- Helping cut down the number of regression bugs that escape to your customers
- Helping your team build what your stakeholders actually need
- Freeing your testers from rote regression tests so they can do more important testing

Note we never once mentioned metrics like “ensure 100% test coverage,” “create 5,000 automated test cases,” or “convert 95% of manual tests to automated.” Those are incredibly awful, horrible, nasty, smelly metrics that in my view have no place in any project. They’re extremely shallow metrics that don’t indicate the value of tests. Make your goals something that’s more effective in helping your team deliver true value to your customers.