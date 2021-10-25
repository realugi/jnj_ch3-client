<template>
  <div>
    <p>{{ description }}</p>
    <p>{{ done }}</p>
  </div>
</template>

<script>
export default {
  name: 'TodoElement',
  props: ['description', 'done']
}
</script>
