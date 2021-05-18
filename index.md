<p align="center">
  <img width="500" src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/Scratchlogo.svg/1024px-Scratchlogo.svg.png" alt="Scratch Logo">
</p>
<p align="center">
Bookmarklets!
</p>

this site is all about bookmarklets for scratch! below is some javascript you can bookmark to change/improve scratch
-----
this bookmarklet makes newlines when you press enter while you make a comment!

thanks to [Raihan142857](scratch.mit.edu/users/Raihan142857) for making this code!
```javascript
javascript:const canvas = document.createElement('canvas');
document.body.appendChild(canvas);
const ctx = canvas.getContext('2d'); // you need a canvas context to measure text length
ctx.font = '13px / 18px "Helvetica Neue", Helvetica, Arial, sans-serif';
document.onclick = () => {
  Array.from(document.querySelectorAll('textarea[name=content]')).forEach((comment) => { // loops through all the comments
    comment.addEventListener('keypress', (e) => {
      if ((e.key === 'Enter' || e.keyCode === 13) && !comment.value.endsWith('\u2003')) { // does stuff when you hit enter while writing the comment
        const maybeReply = comment.parentNode.parentNode.parentNode.dataset.content === 'reply-form' ? 0.8 : 1; // check if it's a reply and adjust is accordingly
        const textLength = ctx.measureText(comment.value.slice(comment.value.lastIndexOf('\u2003') + 1)).width; // calculate the length of the text
        comment.value += '\u2003'.repeat(Math.max(0, Math.floor(maybeReply * (-0.08 * textLength + 36)))); // this is the magic part that insertss the newline
        comment.parentNode.parentNode.querySelector('a').onclick = () => {
          comment.value = comment.value.replace(/ /g, '\u00a0'); // when the comment is posted all spaces need to be non-breaking to make it work
        };
      }
    });
  });
};
document.onclick();
```
CST1229 bookmarks
----
this is the chapter in the book all about CST's bookmarks!
now how do i make a good transition?

Let's be honest, who uses the Clean button in the Scratch forums? Nobody! This is why I've created this bookmarklet, which replaces the Clean button with a Code button.
Just click it and now your Clean button is now a Code button that adds code tags to your text!
I would have liked to reorder it to be next to the Quote button but that's a bit hard to do.

thanks to [CST1229](scratch.mit.edu/users/CST1229) for making this code!
```javascript
javascript:mySettings.markupSet[21].replaceWith.delete;mySettings.markupSet[21].openWith="[code]";mySettings.markupSet[21].closeWith="[/code]";var codeButton=document.getElementsByClassName("markItUpButton15")[0].childNodes[0];codeButton.title="Code";codeButton.innerHTML="Code";console.log("Loaded Clean -> Code bookmarklet")
```
now the thing you have been waiting for. The original post button!
when you quote a post, it will automatically add a link to the original post.

thanks to [CST1229](scratch.mit.edu/users/CST1229) for making this code!
```javascript
javascript:function copy_paste(id){var post=$('#'+id);var username=post.find(".username").text();$.ajax('/discuss/post/'+id.substr(1)+'/source/').done(function(data){paste('[quote='+username+']'+data+'\n[url=scratch.mit.edu/discuss/post/'+id.substring(1)+'][small][i][color=#888888][[]Original post][/color][/i][/small][/url]'+'[/quote]\n');});}console.log("Loaded [Original post] bookmarklet");

```

cst is probably doing more bookmarks so imma put more of them here!
