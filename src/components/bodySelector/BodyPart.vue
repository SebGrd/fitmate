<template>
  <g
    ref="part"
    class="body-part"
    @click="$emit('click', {id, name, category: category ? category : 0})">
    <slot></slot>
  </g>
</template>

<script>
export default {
  name: "BodyPart",
  props: {
    id: {
      type: Number,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    category: {
      type: Number,
    },
  },
  methods: {
    select() {
      this.$refs.part.classList.add('body-part--active')
    },
    unselect() {
      this.$refs.part.classList.remove('body-part--active')
    },
  },
}
</script>

<style scoped>
.body-part{
  cursor: pointer;
}
.body-part:hover *{
  fill: forestgreen!important;
}
.body-part--active *{
  fill: dodgerblue!important;
}
</style>