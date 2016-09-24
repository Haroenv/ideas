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
const dataUrl = 'https://github.com/Haroenv/ideas/edit/gh-pages/_data/ideas.yml';
function createForm() {
  var items = document.getElementById('items');
  const insert = '<form id="form"><input type="submit" value="+"><input type="text" name="idea" id="idea" placeholder="new idea!"></form><pre id="hidden"></pre><button id="copy">execute</button>';
  const item = document.createElement('li');
  item.innerHTML = insert;
  items.appendChild(item);

  var form = document.getElementById('form');
  form.addEventListener('submit', function(e) {
    e.preventDefault();
    const newElement = {
      text: e.target.idea.value,
      checked: false
    };
    const newElementYaml = '- checked: false\n  text: '+e.target.idea.value;
    hidden.textContent = newElementYaml;
    copy.focus();
  });
  copy.addEventListener('click', function(e) {
    e.preventDefault();
    if (copyEl(hidden)) {
      location.href = dataUrl;
    }
  });
}

function copyEl(element) {
  console.log(element);
  var range = document.createRange();
  range.selectNode(element);
  window.getSelection().addRange(range);
  try {
      var copy = document.execCommand('copy');
      return copy;
  } catch (err) {
      throw 'Oops, unable to copy';
  }
  window.getSelection().removeAllRanges();
}
if (localStorage.user === 'haroen') {
  createForm();
}
</script>
