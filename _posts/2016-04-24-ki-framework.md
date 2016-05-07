---
layout: post
title: ki framework
---

Is a tiny ruby framework built for fast prototyping web applications.

It comes with:

* mongoDB for the database
* a REST API for your models
* WebSockets support for realtime communication
* auto-generating documentation
* auto-generating admin interface

Inspired by Rails and Sinatra, this framework aims to make you write **the least amount of code possible**. It plays well with mobile, client side frameworks (ex: Angular) and deployment is standard (similar to Rails/Sinatra).

### example app

This todo application requires a title and a description, the title is unique and deleting items is not allowed.

{% highlight ruby %}
class Todo < Ki::Model
  requires :title, :description
  unique :title
  forbid :delete

  def before_all
    puts 'i am called before all requests'
  end

  def before_create
    params['created_at'] = Time.now.to_i
  end

  def after_find
    puts 'i am called after find'
  end
end
{% endhighlight %}

The application generates a full-blown RESTful api for each class which extends Ki::Model.

 Verb | Url         |Required params|
------|-------------|---------------|
GET   | /todo.json  |               |
POST  | /todo.json  |               |
PATCH | /todo.json  | id            |
DELETE| /todo.json  | id            |

For realtime communication, ki uses WebSockets. Users connect to ki at the */realtime* WebSocket endpoint and subscribe to channels. Once subscribed, they will receive all the messages from their channels. [Read more about realtime](https://github.com/mess110/ki/blob/master/REALTIME.md).

# tutorial

Here is a [tutorial](https://github.com/mess110/ki#install) which will take you though ki features.

Example applications built with ki:

* [json cloud storage](https://json.northpole.ro/)
* [rhubarb](http://rhubarb.northpole.ro/#/)
* [mango](https://json.northpole.ro/app/build/index.html#/tutorial) - note: no client side encryption yet.
