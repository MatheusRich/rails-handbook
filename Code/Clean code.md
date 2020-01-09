# Writing clean code

- links to external articles:
* https://thoughtbot.com/blog/back-to-basics-solid
* https://medium.com/launch-school/the-basics-of-oop-ruby-26eaa97d2e98
https://blog.alexdevero.com/6-simple-tips-writing-clean-code/
https://medium.com/mindorks/how-to-write-clean-code-lessons-learnt-from-the-clean-code-robert-c-martin-9ffc7aef870c


We strive to write code that conforms to the four rules for developers by [Sandi Metz](http://www.sandimetz.com/):

1. Classes can be no longer than one hundred lines of code.
2. Methods can be no longer than five lines of code.
3. Pass no more than four parameters into a method. Hash options are parameters.
4. Controllers can instantiate only one object. Therefore, views should only know about one instance variable.

Please read an [article](https://robots.thoughtbot.com/sandi-metz-rules-for-developers) on these four rules.

You may find it difficult to conform to the fourth rule. In general, whenever you think you might be breaking a rule, follow this:

1. Don't violate a guideline without a good reason.
2. A reason is good when you can convince a teammate.

Since it's often difficult, just remember that it was created because of controller actions like [this one](https://gist.github.com/DamirSvrtan/889133405cf02e4327e0).

Other guidelines

* [Avoid writing class methods](http://blog.codeclimate.com/blog/2012/11/14/why-ruby-class-methods-resist-refactoring/)—they resist refactoring and are better as extracted objects with one public method and multiple privates than as a single class method.
Class methods should be used only for describing a rule that is applied to all instances:

```Ruby
class Order
  def self.policy_class
    OrderPolicy
  end
end
```

* Avoid writing local variables — most local variables are better as extracted methods.

# Maintaining clean code

Once in a while, you'll face the challenge of adding a feature to a legacy project. Please follow these rules:

* Follow the **Boy Scout Rule** — always leave the code behind in a better state than you found it. If you're working with a legacy codebase, try to leave the code you're touching in a better state by not doing hacks, but rather adapting the code to conform to the new feature requirements. Thinking you'll do the refactoring later is wrong because that never happens.
* There is an exception to the previous rule. Don't refactor untested code that works — you'll probably break it. The best way would be to test the code that you're working with, and then refactor it. If it is not possible to write tests for the part of the legacy code you're working with, just use the code as is.

