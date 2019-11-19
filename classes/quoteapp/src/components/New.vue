<template>
  <div>
    <h3>New Quote</h3>
    <p>{{ counter }}</p>
    <button @click="counter++">Increase</button>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      counter: 0
    };
  },
  deactivated(){
    
  }
};
</script>
