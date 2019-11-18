  ## W10D1 - Rails Review & Going further

### Review

Let's talk !

#### Namespacing & Nested Routing
We reviewed good practices for nested routing and talked about why we should use namespaces in our projects

https://guides.rubyonrails.org/routing.html#controller-namespaces-and-routing

#### Ruby Scalability
One of the main issue that people are complaining about is about Rails and Ruby are slow. However, this is mostly based on older versions and newer versions are getting faster and the rumored 3.x versions should be pretty fast.

### What's possible now ?

#### Since Rails 5.0
Released in 2016, this new version added a lot of great features that helped better structure the templating aspects of Rails, and made it more flexible with data only structures and remote work.

https://weblog.rubyonrails.org/2016/6/30/Rails-5-0-final/

##### UJS, or unobstrusive JavaScript
It is now possible to use CoffeeScript (by default, but you should use JS) or JavaScript methods not directly embedded in the template files (hence the unobstrusive) to make a cleaner template structure. It also has great helpers for remote work (ajax).

https://guides.rubyonrails.org/working_with_javascript_in_rails.html#unobtrusive-javascript

##### ActionCable
ActionCable is a very great integration of WebSockets inside your Rails app, so you can leverage the Pub/Sub approach to different channels easily without having to fiddle with a WebSocket library.

Demo in the actioncable-examples folder
https://guides.rubyonrails.org/action_cable_overview.html

##### API mode
Since we move towards a more decoupled future in our apps, Rails implemented an API mode when you create a new project that will make sure you don't have a superfluous folder and file structure.

#### Since Rails 6.0
Released a little less than two weeks ago (15th of August 2019), this new version updates a couple of things and has some great changes, some of them are enumarated here :

https://weblog.rubyonrails.org/2019/8/15/Rails-6-0-final-release/

##### ActionMailbox
It's now possible to manage email traffic in your Rails App and can be used to do a multitude of things like confirming an appointment for the client by replying to the sent message, confirm password change, other 2fa possibilities, etc.

https://edgeguides.rubyonrails.org/action_mailbox_basics.html

##### ActionText
It's possible to integrate a rich text editor in the erb templates now :

###### Model
```
class Message < ApplicationRecord
  has_rich_text :content
end
```
###### Form
```
<%# app/views/messages/_form.html.erb %>
<%= form_with(model: message) do |form| %>
  <div class="field">
    <%= form.label :content %>
    <%= form.rich_text_area :content %>
  </div>
<% end %>
```
###### Display
```
<%= @message.content %>
```
https://edgeguides.rubyonrails.org/action_text_overview.html
RTE used : https://trix-editor.org/

##### Truncate database

You can now truncate your database without having to delete everything ! Yay !
```
rails db:truncate_all
``
