<template>
  <div id="app">
    FacebookStyle:
    <FacebookStyle />
    InstagramStyle:
    <InstagramStyle />
    CodeStyle:
    <CodeStyle />
    ListStyle:
    <ListStyle />
    BulletListStyle:
    <BulletListStyle />
    ContentLoader:
    <ContentLoader />
  </div>
</template>

<script>
/* eslint-disable */
import { FacebookStyle, InstagramStyle, CodeStyle, ListStyle, BulletListStyle, ContentLoader } from './components/ContentLoader/index.js';
export default {
  name: 'app',
  components: {
    [FacebookStyle.name]: FacebookStyle,
    [InstagramStyle.name]: InstagramStyle,
    [CodeStyle.name]: CodeStyle,
    [ListStyle.name]: ListStyle,
    [BulletListStyle.name]: BulletListStyle,
    [ContentLoader.name]: ContentLoader
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 600px;
  margin: auto;
}
</style>
