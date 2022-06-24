<template>
  <button :disabled="disabled" class="btn" :class="[varient ? `btn-${varient}` : '', size ? `btn-${size}` : '']" @click="this.$emit(`onClick`)">{{ title }}</button>

  <!-- <button class="btn" :class="[variant ? `btn-${variant}`:``, size ? `btn-${size}` : ``, style ? `btn-circled` : ``]" @click="this.$emit(`onClick`)">
        <template v-if="title">{{ title }}</template>
        <template v-if="iconName">
            <font-awesome-icon :icon="['fas', `${iconName}`]" />
        </template>
    </button> -->
</template>
<script>
export default {
  props: ['title', 'varient', 'size', 'disabled']
}
</script>
