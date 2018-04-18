<template>
  <div>
    <div v-for="item in feed" class="item">
      <p class="idline"><span class="user">Department: {{item.name}}</span><router-link :to="{ name: 'UserPage', params: {userID: item.userID}}"></router-link></p>
      <p v-html="formatTweet(item.tweet)" class="tweet"></p>
      
    </div>
  </div>
</template>

<script>
 import moment from 'moment';
 import linkify from './linkify.js';
 export default {
   name: 'FeedList',
   props: ['feed'],
   filters: {
     since: function(datetime) {
       moment.locale('en', {

       });
       return moment(datetime).fromNow();
     },
   },
   methods: {
     formatTweet: function(text) {
       return linkify(text, {
         defaultProtocol: 'https'
       });
     },
   },
 }

</script>

<style scoped>
 .item {
     border-bottom: 1px solid #ddd;
     padding: 10px;
 }
 .tweet {
     margin-top: 0px;
 }
 .idline {
     margin-bottom: 0px;
     font-weight: bold;
     font-size: 150%;
 }
 .user {
     font-weight: bold;
     margin-right: 10px;
 }
 .handle {
     margin-right: 10px;
     color: #666;
 }
 .time {
     float: right;
     color: #666;
 }
</style>
