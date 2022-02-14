<template>
    <div class="space-x-1">
        <div class="flex justify-center w-full">
            <h2 class="text-black font-serif m-4">Top User</h2>
            <search @search="search"/>
        </div>
        <!-- <div>
            <h2>A basic HTML table</h2>
                <table style="width:100%">
                    <tr>
                        <th class="px-6 py-3 text-left text-xs font-medium text-black uppercase tracking-wider">Company</th>
                        <th lass="px-6 py-3 text-left text-xs font-medium text-black uppercase tracking-wider">Contact</th>
                        <th lass="px-6 py-3 text-left text-xs font-medium text-black uppercase tracking-wider">Country</th>
                    </tr>
                    <tr>
                        <td>Alfreds Futterkiste</td>
                        <td>Maria Anders</td>
                        <td>Germany</td>
                    </tr>
                    <tr>
                        <td>Centro comercial Moctezuma</td>
                        <td>Francisco Chang</td>
                        <td>Mexico</td>
                    </tr>
                </table>
                <p>To undestand the example better, we have added borders to the table.</p>
        </div> -->
        <!-- <table class="table-auto">
            <thead class="text-black">
                <tr>
                    <th>bsav</th>
                    <th>Artist</th>
                    <th>Year</th>
                </tr>
            </thead>
            <tbody>
                <tr class="text-black" v-for="item in searchData" :key="item.id">
                <td>The Sliding Mr. Bones (Next Stop, Pottersville)</td>
                <td>Malcolm Lockyer</td>
                <td>1961</td>
                </tr>
            </tbody>
        </table> -->
        <div class="flex flex-col w-full">
        <div class="my-2 overflow-x-auto">
            <div class="py-2 align-middle inline-block min-w-full">
            <div class="shadow overflow-hidden border-b border-green-500 sm:rounded-lg">
                <table class="">
                <thead class="bg-gray-50">
                    <tr>
                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-black uppercase tracking-wider">Avatar</th>
                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-black uppercase tracking-wider">ID</th>
                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-black uppercase tracking-wider">Events</th>
                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-black uppercase tracking-wider">followers</th>
                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-black uppercase tracking-wider">following</th>
                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-black uppercase tracking-wider">gists</th>
                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-black uppercase tracking-wider">gravatar</th>
                    </tr>
                </thead>
                <tbody class="bg-transparent divide-y divide-gray-200">
                    <tr v-for="item in searchData" :key="item.id">
                        <td class="px-6 py-4 whitespace-nowrap">
                            <div class="flex items-center">
                                <div class="flex-shrink-0 h-10 w-10 text-black">
                                    {{item.avatar_url}}
                                </div>
                            </div>
                        </td>
                        <!-- <td class="px-6 py-4 whitespace-nowrap">
                            <div class="flex items-center">
                                <div class="flex-shrink-0 h-10 w-10 text-black">
                                    {{item.events_url}}
                                </div>
                            </div>
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap">
                            <div class="flex items-center">
                                <div class="flex-shrink-0 h-10 w-10 text-black">
                                    {{item.followers_url}}
                                </div>
                            </div>
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap">
                            <div class="flex items-center">
                                <div class="flex-shrink-0 h-10 w-10 text-black">
                                    {{item.following_url}}
                                </div>
                            </div>
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap">
                            <div class="flex items-center">
                                <div class="flex-shrink-0 h-10 w-10 text-black">
                                    {{item.gists_url}}
                                </div>
                            </div>
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap">
                            <div class="flex items-center">
                                <div class="flex-shrink-0 h-10 w-10 text-black">
                                    {{item.gravatar_id}}
                                </div>
                            </div>
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap">
                            <div class="flex items-center">
                                <div class="flex-shrink-0 h-10 w-10 text-black">
                                    {{item.html_url}}
                                </div>
                            </div>
                        </td> -->
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