<template>
  <div class="home">
    <ArticleForm/>
  </div>
</template>

<script>
// @ is an alias to /src
import ArticleForm from '@/components/ArticleForm.vue'

export default {
  name: 'Create',
  components: {
    ArticleForm
  }
}
</script>
