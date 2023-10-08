<template>
  <div class="my-tag">
    <input type="text"
      v-if="isEdit"
      v-focus
      ref="inp"
      class="input"
      placeholder="输入标签"
      :value="value"
      @blur="isEdit = false"
      @keyup.enter="handleEnter"
    >
    <div
      v-else
      @dblclick="handleClick"
      class="text">{{ value }}</div>
  </div>
</template>
<script>
export default{
  name: 'APP',
  props: {
    value: String
  },
  data () {
    return {
        isEdit: false
    }
  },
  methods:{
    handleClick(){
      this.isEdit = true
    },
    handleEnter(e){
      if(e.target.value.trim() === ''){
        alert('内容不能为空')
        return
      }
      this.$emit('input',e.target.value)
      this.isEdit = false
    }
  }
}
</script>
<style lang="less" scoped>
.my-tag {
  cursor: pointer;
  .input{
    appearance: none;
    outline: none;
    border: 1px solid #ccc;
    width: 100px;
    height: 40px;
    box-sizing: border-box;
    padding: 10px;
    color: #666;
    &::placeholder {
      color: #666;
    }
  }
}
</style>