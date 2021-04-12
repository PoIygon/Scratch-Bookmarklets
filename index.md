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
document.onclick();```
