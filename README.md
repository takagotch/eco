### eco
---
https://github.com/sstephenson/eco/

```
<% if @projects.length: %>
  <% for project in @projects: %>
    <a href="<%= project.url %>"><%= project.name %></a>
    <p><%= project.description %></p>
  <% else: %>
    No projects
<% end %>

<% if @project.isOnHold(): %>
  On Hold
<% end %>

<% if @project.isOnHold(): %> On Hold <% end %>

<%= "On Hold" if @project.isOnHold() %>

<% if @project.isOnHold(): %>
  On Hold
<% else if @project.isArchived(): %>
  Archived
<% end %>
```

```js
eco = require "eco"
fs = require "fs"
template = fs.readFileSync __dirname + "/views/projects.html.eco", "utf-8"
console.log eco.render template, projects: [
  { name: "Mobile app", "/projects/1", description: "Iteration 1" },
  { name: "Home page redesign", url: "/projects/2" }
]

eco.render "<p><%= @description %></p>",
  description: "HTML 5 mobile app"
  
translations = require "translations"
eco.render "<span><%= @translate 'common.welcomeText' %></span>",
  language: "en"
  translate: (key) ->
    translations[@language][key]

echo.render "<%= @description %>",
  description: "<strong>HTML 5</strong> mobile app"

&lt;strong&gt;HTML 5&lt;/strong&gt; mobile app

eco.render "<%- @description %>",
  description: "<strong>HTML 5</strong> mobile app"

eco.render "<%= @linkTo @project %>",
  project: { id: 4, name: "Create & Barrel" }
  linkTo: (project) ->
    url = "/projects/#{project.id}"
    name = @escape project.name
    @safe "<a href='#{url}'>#{name}</a>"
```

```
```

