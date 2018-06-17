---
title: Contact Us
---

<style>
 input, textarea {
    width:300px;
    font-size: 0.8em;
    font-family: 'proxima-nova-soft', sans-serif; 
    border: 1px solid #ddd; 
    background: #fff; 
    padding: 0.9em;
    transition: all 0.3s ease-in-out;
 }
 button {
    font-size: 1em;
    text-transform: uppercase;
    font-weight: 600;
    border: 2px solid #0040b0;
    color: #0040b0;
    background: transparent;
    line-height: 1em;
    padding: 0.6em 0.9em;
    transition: all 0.3s ease-in-out;
 }
</style>
<form id="formaction" method="POST">
  <div style="width:100%; margin:10px">
    <input type="email" name="email" placeholder="email@domain.com">
  </div>
  <div style="width:100%; margin:10px">
    <textarea name="message" placeholder="Message" style="height:100px"></textarea>
  </div>
  <div style="width:100%; margin:10px">
    <button type="submit">Send</button>
  </div>
</form>
<script>
    var contactform =  document.getElementById('formaction');
    contactform.setAttribute('action', '//formspree.io/' + 'contact' + '@' + 'stemalliancefm' + '.' + 'org');
</script>