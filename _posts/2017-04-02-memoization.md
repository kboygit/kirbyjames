---
layout: inner
title: 'MEMOIZATION IN RUBY'
date: 2017-04-02 05:56:48
categories: Self-Development
tags: Ruby Rails RubyGems Memoization
lead_text: 'If you wanna go fast go alone , if you want to go further go with a team.'
---

Memoization or memoisation is an optimization technique used primarily to speed up computer programs by storing the results of expensive function calls and returning the cached result when the same inputs occur again.

Memoization has also been used in other contexts (and for purposes other than speed gains), such as in simple mutually recursive descent parsing[1] in a general top-down parsing algorithm[2][3] that accommodates ambiguity and left recursion in polynomial time and space. Although related to caching, memoization refers to a specific case of this optimization, distinguishing it from forms of caching such as buffering or page replacement. In the context of some logic programming languages, memoization is also known as tabling.

First encounter on memoization pattern in ruby:

For this instance inside the namespaced controller sections_controller.rb from instructor
{% highlight ruby %}
# app/controllers/instructor/sections_controller.rb

helper_method :current_course
def current_course
    @current_course ||= Course.find(params[:course_id])
end
{% endhighlight %}

        @current_section ||=

This single line of code is a shortcut and will do the same thing as the multiple lines below:

{% highlight ruby %}
if @current_section == nil
    @current_section = Section.find(params[:section_id])
    @current_section
else
    @current_section
end
{% endhighlight %}

{% highlight ruby %}
In short, this single line '@current_section ||=' says: if we've looked up the current_section beforehand use the value that we looked up previously. If we haven't looked up this section before, go into the database, look it up and also make sure to remember the value in case we need to look it up again later. This technique of storing certain values inside of the memory to reduce the times we have to find a certain value inside the database is called memoization/memoisation.

The '||=' more or less translates to '@current_course = @current_course || current_course.user'. That means that you’ll only make the network call the first time you call current_course, and future calls will just return the value of the instance variable '@current_course'.
{% endhighlight %}

## Resources to read more about ruby memoization:

- [4 simple memoization patterns](http://www.justinweiss.com/articles/4-simple-memoization-patterns-in-ruby-and-one-gem/)
- [Memoization in ruby](https://atech.blog/atech/memoization-in-ruby)
- [Basics of ruby memoization](http://gavinmiller.io/2013/basics-of-ruby-memoization/)
- [Advanced memoization in ruby](http://gavinmiller.io/2013/advanced-memoization-in-ruby/)
