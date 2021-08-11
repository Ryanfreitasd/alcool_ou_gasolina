<template>
  <div id="message-container">
    <span>{{props.result}}</span>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Message',
  props: {
    result: String
  },
  setup(props) {
    return {
      props
    }
  },
})
</script>
<style lang="scss" scoped>
 #message-container {
   width: 100%;
   margin: 0px 20px;
   padding: 5px;
   height: 50px;
   background-color: $primary;
   color: #fff;
   border-radius: 5px;
   display: flex;
   flex-direction: column;
   justify-content: center;
   align-items: center;
 }

 #message-container span {
   font-weight: bold;
   font-size: 18px;
 }
</style>
