---
layout: index
---

<ul id="items">
{% for idea in site.data.ideas %}
<li><input type="checkbox" disabled {% if idea.checked %}checked{% endif %}> {{idea.text | markdownify | remove: '<p>' | remove: '</p>' }}</li>
{% endfor %}
</ul>

All these ideas are free of charge, but I'd appreciate it if you let me know that it became reality.

Ping me on twitter [@Haroenv](https://twitter.com/Haroenv)


<script>
function createForm() {
  var items = document.getElementById('items');
  const insert = '<form id="form"><input type="submit" value="+"><input type="text" name="idea" id="idea" placeholder="new idea!"></form>';
  const item = document.createElement('li');
  item.innerHTML = insert;
  items.appendChild(item);
}
if (localStorage.user === 'haroen') {
  createForm();
}
</script>
