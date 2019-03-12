<template>
   <div class="post-meta">
      {{ post.date }} 发布.
      <template v-if="post.timeToRead">
        <strong>{{ post.timeToRead }}分钟前阅读.</strong>
      </template>
    </div>
</template>

<script>
export default {
  props: ['post']
}
</script>

<style lang="scss">
.post-meta {
  font-size: .8em;
  opacity: .8;
}
</style>