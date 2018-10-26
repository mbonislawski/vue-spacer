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
     max-width: 600px;
 }

 .claim {
     font-size: 50px;
     margin: 0;
     @media(min-width: 767px) {
         font-size: 80px;
     }
 }

 .subclaim {
     margin: 20px 0 0 0;
     font-size: 14px;
     font-weight: 400;
 }
</style>