<template>
  <div class="feed">
    <div class="myfee">
    <h1>Inventory Logging</h1>
    <img src="/static/images/stock.jpg"/>
          <br><br><br>
      <form v-on:submit.prevent="tweet" class="tweetForm">
	<textarea v-model="text" placeholder="Product"/><br/>
  <textarea v-model="text2" placeholder="Description"/><br/>
  <textarea v-model="text3" placeholder="Quantity"/><br/>
  <textarea v-model="text4" placeholder="msrp"/><br/>
	<div class="buttonWrap">
	  <button class="primary" type="submit">Submit</button>
	</div>
      </form>

    </div>
    <feed-list v-bind:feed="feed" />
  </div>
</template>

<script>
 import FeedList from './FeedList';
 export default {
   name: 'UserFeed',
   data () {
     return {
        text: '',
        text2: '',
        text3: '',
        text4: '',
     }
   },
   components: { FeedList },
   computed: {
     feed: function() {
       return this.$store.getters.feed;
     },
   },
   created: function() {
     this.$store.dispatch('getFeed');
   },
   methods: {
     tweet: function() {
       this.$store.dispatch('addTweet',{
         tweet: "Product: \n" + this.text + "\n\nDescription:\n" + this.text2 + "\n\nQuantity:\n" + this.text3 + "\n\nMSRP:\n" + this.text4,
       }).then(tweet => {
      	 this.text = "";
         this.text2 = "";
         this.text3 = "";
         this.text4 = "";
       });
     },
   }
 }
</script>

<style scoped>
 .feed {
     width: 100%;
 }
 .tweetForm {
     background: #007dc6;
     padding: 10px;
     margin-bottom: 10px;
     margin-left: 25%;
     margin-right: 25%;
     margin-bottom: 5%;
 }
 .buttonWrap {
     width: 100%;
     display: flex;
 }
 button {
     margin-left: auto;
     height: 2em;
     font-size: 0.9em;
 }
 textarea {
     width: 100%;
     height: 5em;
     padding: 2px;
     margin-bottom: 5px;
     resize: none;
     box-sizing: border-box;
 }
 .myfee {
  text-align: center;
 }
 img {
 width: 70%;
 }
  h1 {
     margin-bottom: 0px;
     color: #007dc6;
 }
</style>
