<template>
  <div class="searchWrapper">
      <input 
        name="search" 
        :class="{ dark: dark }"
        id="search" 
        :value="value"
        @input="handleChange"
        />
  </div>
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
      value: {
          type: String,
          required: true,
      },
      dark: {
          type: Boolean,
          default: false,
    },
  },
  methods: {
      handleChange(e) {
          this.$emit('input', e.target.value);
      },
  },
};
</script>
<style lang="scss" scoped>
.searchWrapper {
    display: flex;
    flex-direction: column;
    width: 250px;

    input {
      height: 30px;
      border: 0;
      border-bottom: 1px solid white;
      background: none;
      outline: 0;
      text-align: center;
      margin-top: 40px;
      color: #fff;
      font-size: 16px;
      transition: box-shadow .3s;
      margin-top: 60px;
      padding: 5px;
    }

    input:focus {
        box-shadow: 0 10px 20px -11px rgba(255,255,255, 0.5);
    }

    .dark {
        color: #000;
        border-bottom: 1px solid black;

        &:focus {
            box-shadow: 0 10px 20px -8px rgba(0,0,0, 0.5);
        }
    }
  }
</style>