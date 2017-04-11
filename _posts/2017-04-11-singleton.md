---
layout: inner
title: 'SINGLETON ROUTES'
date: 2017-04-11 12:56:48
categories: Self-Development
tags: Ruby Rails
lead_text: 'If you wanna go fast go alone , if you want to go further go with a team.'
---

Resources in routes.rb, there is also a singular or singleton form of resource routing(resource :) . It's used to represent a resource that only exists once in its given context.

A singleton resource route at the top level of your routes can be appropriate when there's only one resource of its type for the whole application, perhaps something like a per-instructor dashboard, which in my case is.

Sometimes, you have a resource that clients always look up without referencing an ID. A common example, /dashboard always shows the dashboard of the currently logged in instructor/user. In this case, you can use a singular resource to map /dashboard (rather than /dashboard/:id) to the show action:

        resource :dashboard, only: [:show]

creates six different routes in your application, all mapping to the Dashboards controller (note that the controller is named after the plural):

        GET       /dashboard/new
        POST      /dashboard
        GET       /dashboard
        GET       /dashboard/edit
        PATCH/PUT /dashboard
        DELETE    /dashboard

Rather than using the command resources, the command resource is used.
When specifying the name of the controller we're linking to specify the singular version of the word, even though the controller name we generated is plural. In this case it will connect to our dashboards controller knowing we specified :dashboard in the routes. Then you will see this on your routes.

        dashboard GET /dashboard(.:format)      dashboards#show

It's assumed that you're in a context where it's meaningful to speak of the dashboard—the one and only—because there's an instructor to which the dashboard is scoped. The scoping itself is not automatic; you have to authenticate the instructor/user and retrieve the dashboard from (and/or save it to) the database explicitly. There's no real magic or mind-reading here; it's just an additional routing technique at your disposal if you need it.


## Read more on routing

- [Routing Guides](http://guides.rubyonrails.org/v2.3/routing.html)
- [Apidock Resource](https://apidock.com/rails/ActionController/Resources/resource)
- [Resources vs. Resource](https://apidock.com/rails/ActionDispatch/Routing/Mapper/Scoping/Resources/resources)
