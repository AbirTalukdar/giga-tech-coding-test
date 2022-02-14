<template>
    <div class="space-x-1">
        <div class="flex justify-center w-full">
            <h2 class="text-black font-serif m-4">Top User</h2>
            <search @search="search"/>
        </div>
        <div class="flex flex-col w-auto">
        <div class="my-2 overflow-x-auto">
            <div class="py-2 align-middle inline-block min-w-full">
            <div class="shadow border-b border-green-500 sm:rounded-lg">
                <table class="">
                <thead class="bg-gray-50">
                    <tr>
                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-black uppercase tracking-wider">Avatar</th>
                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-black uppercase tracking-wider">ID</th>
                    </tr>
                </thead>
                <tbody class="bg-transparent divide-y divide-gray-200" v-for="item in searchData" :key="item.id">
                    <tr>
                        <td class="px-6 py-4 whitespace-nowrap">
                            <div class="flex items-center">
                                <div class="flex-shrink-0 h-10 w-10 text-black">
                                    <img :src="item.avatar_url">
                                </div>
                            </div>
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap">
                            <div class="flex items-center">
                                <div class="flex-shrink-0 h-10 w-10 text-black">
                                    {{item.id}}
                                </div>
                            </div>
                        </td>
                    </tr>
                </tbody>
                </table>
            </div>
            </div>
        </div>
        </div>
    </div>
</template>

<style>
    table, th, td {
        border:1px solid black;
    }
</style>

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
            fetch(`https://api.github.com/search/users?q=${searchWord}`, { method: 'GET'})
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