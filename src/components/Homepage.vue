<template>
  <div>
    <composer></composer>
    <tweets-list></tweets-list>
  </div>
</template>

<script>
  import Composer from './Composer';

  export default {
    name: 'homepage',
    components: {
      composer: Composer,
    },
  };
</script>
