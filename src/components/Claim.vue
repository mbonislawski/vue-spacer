<template>
  <div class="claimWrapper">
    <h1 class="claim">SPACER</h1>
    <p class="subclaim">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam eu mollis metus. Curabitur risus nunc, ullamcorper id massa a, aliquam fermentum lorem.</p>
    <p class="subclaim">Type anything space-related to start.</p>
  </div>
</template>

<script>
export default {
  name: 'Claim',
};
</script>
<style lang="scss" scoped>
 .claimWrapper {
     display: flex;
     flex-direction: column;
     justify-content: center;
     align-items: center;
     text-align: center;
 }

 .claim {
     font-size: 50px;
     margin: 0;
 }

 .subclaim {
     margin: 20px 0 0 0;
     font-size: 13px;
 }
</style>