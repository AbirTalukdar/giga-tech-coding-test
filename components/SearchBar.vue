<template>
<div class="mt-2">
    <div class="flex items-center justify-center ">
        <div class="flex border-2 border-gray-200 rounded">
            <input v-model="searchWord" type="text" class="px-4 py-2 w-80 text-black" placeholder="Search...">
            <button v-on:click="initiateSearch" class="px-4 text-white bg-gray-600 border-l ">
                Search
            </button>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data () {
        return {
           searchWord : ''
        }
    },
    methods: {
        initiateSearch (){ 
            this.$emit("search", this.searchWord)
        }
    }
}
</script>