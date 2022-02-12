<template>
    <div class="content-center">
        <h2 class="text-black font-serif">Top Repositories</h2>
        <search />
    </div>
</template>
<script>
import Search from '@/components/SearchBar'
export default {
    components: {
    search: Search
  }
}
</script>