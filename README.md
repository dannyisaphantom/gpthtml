## gpt2html
###### drag to bookmarks bar
```
(function() {
  try {
    const a = document.createElement('a');
    const dom = document.querySelector('main > .flex-1 > .h-full .flex');
    const template = document.createElement('template');
    const title = document.title;
    const non_letters_re = /[^\p{L}\p{N}]+/gu;
    const trailing_dash_re = /(^-)|(-$)/g;
    const slug = title.toLowerCase()
      .replace(non_letters_re, "-")
      .replace(trailing_dash_re, '');
    template.innerHTML = dom.innerHTML;
    ['.items-end', 'img', 'svg', 'button', ':empty'].forEach(selector => {
      template.content.querySelectorAll(selector).forEach(node => {
        node.remove();
      });
    });
    a.href = URL.createObjectURL(new Blob([`<!DOCTYPE html><html><head>  <meta charset="utf-8"/>  <title>Chat GPT: ${title}</title>  <meta name="generator" content="chatGPT Saving Bookmark"/><style>body {  background-color: rgb(32,33,35);  color: rgb(236,236,241);  font-size: 16px;  font-family: sans-serif;  line-height: 28px;  margin: 0;}body > .w-full {  padding: 30px;}/* prompt */body > .w-full:nth-child(2n+1) {  background: rgb(52,53,65);}/* response */body > .w-full:nth-child(2n+2) {  background: rgb(68,70,84);}a, a:visited {  color: #7792cd;}pre%20{%20%20margin:%200%200%201em%200;%20%20display:%20inline-block;%20%20width:%20100%;}pre%20code.hljs%20{%20%20margin-bottom:%201em;%20%20border-radius:%205px;}.whitespace-pre-wrap%20{%20%20white-space:%20pre-wrap;}.flex-col%20{%20%20max-width:%20850px;%20%20margin:%200px%20auto;}%3C/style%3E%3Clink%20rel=%22stylesheet%22%20href=%22https://cdn.jsdelivr.net/gh/highlightjs/cdn-release@11.7.0/build/styles/default.min.css%22/%3E%3C/head%3E%3Cbody%3E${template.innerHTML}%3C/body%3E%3C/html%3E%60],%20{type:%20'text/html'}));
    a.download = `chat-gpt-${slug}.html`;
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
    URL.revokeObjectURL(a.href);
  } catch(e) {
    alert(e.message);
  }
})();

```
