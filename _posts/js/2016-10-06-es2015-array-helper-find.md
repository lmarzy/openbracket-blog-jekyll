---
category: js
---

Let's check out the Array helper of find. The purpose of the find helper is to search through an Array and look for a particular element, as soon as an element is found the helper will return that record.

If you have been writing any JS for a period of time you have probably needed to find a value in an array, and you have probably used a for loop to achieve this as shown:

{% highlight javascript %}
const users = [
  { name: 'Jim' },
  { name: 'Jack' },
  { name: 'Jill'}
];

let user;

for(var i = 0; i < users.length; i++) {
  if (users[i].name === 'Jack') {
    user = users[i];
  }
}
console.log(user); // {name: 'Jack'}
{% endhighlight %}

As you can see we have our Array, in this case we have an Array of Objects and we loop through each item and if we find the user we are looking for we update our variable, we could make this slightly better by adding a 'break;' at the bottom of the if statement to stop the loop continuing once we have a match.

Lets re-create the above now using the Array find helper. The helper works by walking through each element in the Array, each element is then passed into an iterator function which returns a truthy or a falsy value. The find helper will keep calling elements with the iterator function until the function returns true. Once true is returned the find helper immediately exits it's iteration returning the element it finds:

{% highlight javascript %}
const users = [
  { name: 'Jim' },
  { name: 'Jack' },
  { name: 'Jill'}
];

const user = users.find(function(user) {
  return user.name === 'Jack';
});

console.log(user); // {name: 'Jack'}
{% endhighlight %}

As you can see the Array find helper is less code and much easier to read, we could of course get the code even smaller if we wanted using the new ES2015 arrow function syntax:

{% highlight javascript %}
const users = [
  { name: 'Jim' },
  { name: 'Jack' },
  { name: 'Jill'}
];

const user = users.find(user => user.name === 'Jack');

console.log(user); // {name: 'Jack'}
{% endhighlight %}

One thing to bear in mind with this helper is as soon as an element is found in the Array the value is returned, therefore if you have duplicate values in the Array, only the first item that is found will be returned. So if we had two elements in the above with the same name only the first item would be returned:

{% highlight javascript %}
const users = [
  { name: 'Jim', id: 111 },
  { name: 'Jack', id: 222 },
  { name: 'Jill', id: 333 },
  { name: 'Jack', id: 444 }
];

const user = users.find(user => user.name === 'Jack');

console.log(user); // {name: 'Jack', id: 222}
{% endhighlight %}

Give it a try the next time you need to find an element in an Array, you might just like it!

Have fun!
