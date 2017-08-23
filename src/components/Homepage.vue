<template>
  <div>
    <composer></composer>
    <tweets-list></tweets-list>
  </div>
</template>

<script>
  import Composer from './Composer';
  import TweetsList from './TweetsList';

  export default {
    name: 'homepage',
    components: {
      composer: Composer,
      tweetsList: TweetsList,
    },
  };
</script>
