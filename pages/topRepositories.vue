<template>
    <div class="space-x-1">
        <div class="flex justify-center w-full">
            <h2 class="text-black font-serif m-4">Top Repositories</h2>
            <search @search="search"/>
        </div>
    </div>
</template>
<script>
import Search from '@/components/SearchBar'
export default {
    components: {
    search: Search
  },
  data() {
      return{
          searchData: []
      }
  },
    methods: {
        search (searchWord){ 
            fetch(`https://api.github.com/search/repositories?q=${searchWord}`, { method: 'GET'})
            .then(response => response.json()).then( (data) => {
                console.log('data', data)
                console.log(data.items[0].id);
                this.searchData = data.items;
                console.log(this.searchData)
                // let searchData = data.items;
                // console.log();
                // Now we need to bind this data to our table element to show all the results
            })
            // this.searchData.forEach(function(items, index)  {
            //     console.log(items, index)
            //     });
            }
        }
}
</script>