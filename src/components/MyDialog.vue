<template>
  <div class="dialog" v-if="show" @click="hideDialog">
    <div @click.stop class="dialog__content">
      <slot>
      </slot>
    </div>
  </div>
</template>

<script>
import toggleMixin from "@/mixins/toggleMixin";


export default {
  name: "MyDialog",
  mixins: [toggleMixin],
  mounted() {
    console.log('dialog mounted')
  }
}
</script>

<style scoped>
.dialog{
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background-size: 2em 2em;
  position: fixed;
  display: flex;
  background: rgba(0, 0, 0, 0.2);;
}
.dialog__content {
  margin: auto;
  border-radius: 10px;
  min-height: 280px;
  min-width: 375px;
  display: flex;
  align-items: center;
}

</style>