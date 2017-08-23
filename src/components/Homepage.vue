<template>
  <div>
    <composer></composer>
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
