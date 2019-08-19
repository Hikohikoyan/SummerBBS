<template>
  <div class="about">
        <h3>Essential Links</h3>
    <ul>
      <li><a href="http://localhost:8080/about" target="_blank" rel="noopener">About</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>

    <h1>This is an about page</h1>
    <showstatus pagename="about" islogin="false"/>
  </div>
</template>
<script>
  export default {
  name: 'about',
    }
</script>