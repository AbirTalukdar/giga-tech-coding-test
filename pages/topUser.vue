<template>
    <div class="space-x-1">
        <div class="flex justify-center w-full">
            <h2 class="text-black font-serif m-4">Top User</h2>
            <search @search="search"/>
        </div>
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
        <div class="flex flex-col">
        <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
            <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
            <div class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg">
                <table class="min-w-full divide-y divide-gray-200">
                <thead class="bg-gray-50">
                    <tr>
                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Avatar</th>
                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">ID</th>
                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Events</th>
                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">followers</th>
                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">following</th>
                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">gists</th>
                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">gravatar</th>
                    
                    </tr>
                </thead>
                <tbody class="bg-white divide-y divide-gray-200">
                    <tr v-for="item in searchData" :key="item.id">
                    <td class="px-6 py-4 whitespace-nowrap">
                        <div class="flex items-center">
                        <div class="flex-shrink-0 h-10 w-10">
                            {{item.avatar_url}}
                        </div>
                        <div class="ml-4">
                            <div class="text-sm font-medium text-gray-900">{{item.starred_url}}</div>
                            <div class="text-sm text-gray-500">jane.cooper@example.com</div>
                        </div>
                        </div>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap">
                        <div class="text-sm text-gray-900">Regional Paradigm Technician</div>
                        <div class="text-sm text-gray-500">Optimization</div>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap">
                        <span class="px-2 inline-flex text-xs leading-5 font-semibold rounded-full bg-green-100 text-green-800"> Active </span>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">Admin</td>
                    <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">
                        <a href="#" class="text-indigo-600 hover:text-indigo-900">Edit</a>
                    </td>
                    </tr>

                    <!-- More people... -->
                </tbody>
                </table>
            </div>
            </div>
        </div>
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