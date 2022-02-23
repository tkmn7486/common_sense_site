<template>
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <div class="app">
    <div class="title">
      <!-- <img class="logo" alt="logo" src="./assets/logo.png"> -->
      <h2 class="logo">コモセン.WEB</h2>
    </div>
    <div id="nav">
      <router-link to="/">おすすめ</router-link>
      <router-link to="/about">ジャンル別</router-link>
      <router-link to="/about">このサイトについて</router-link>
      <router-link to="/about">ご提案・お問合せ</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
*{
  margin: 0px;
  padding: 0px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: rgba(38,56,89,1);
}

#nav {
  padding: 15px;
  text-align:center;
  background-color:rgba(23,34,59,1);
  border:double 5px #6b778d;
  border-right:none;
  border-left:none;
  border-bottom:none;
}

#nav a {
  margin:0 10px 0 10px;
  font-weight: bold;
  color: #6b778d;
}

router-link{
  margin-left:20px;
}

#nav a.router-link-exact-active {
  color: rgba(255,103,104,1);
}

.title{
  background-color:rgba(23,34,59,1);
  padding:10px;
}

.logo{
  padding-left:10px;
  color:white;
}

/* スマホ用CSS */
@media screen and (max-width:480px) {

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#nav {
  padding: 10px;
  text-align:center;
  border-right:none;
  border-left:none;
  border-bottom:none;
}

#nav a {
  font-size:11px;
  margin:0 10px 0 10px;
  font-weight: bold;
}

router-link{
  margin-left:20px;
}

.title{
  padding:10px;
}

.logo{
  padding-left:10px;
}

}
</style>
