```
Ember: 2.13.4
```

Embe ```route(transitionTo)``` vs ```'-routing'(transitionTo)```

```-routing``` is private service, whenever we want to inject the router inside in the component we use ```-routing``` service 
so that, we can use ```transitionTo``` or any other function inside the component.

but there is slightly difference between genenal ```route(transitionTo)``` and ```'-routing'(transitionTo)``` method,
when we have dynamic segments to be passed.

Let say we the routes with dynamic segments like:
```
this.route('todo', {path:'/:todo_id'},function(){
  this.route('items',function(){
    this.route('new',function(){
    });
  });
});
```
and if we want to transition to route ```todo.items.new``` with the with ```todo_id: 1```, let see how can we use the ```transitionTo``` from both route as well as -routing service

in route:
```
transitionTo('todo.items.new', 1)
```
in ```-routing``` service
```
transitionTo('todo.items.new', [1]); ### We used array to pass the dynamic segments
```

for more infocheck this [issue](https://github.com/emberjs/ember.js/issues/12719)
