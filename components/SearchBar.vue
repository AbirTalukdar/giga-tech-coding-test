<template>
<div class="mt-2">
<div class="flex items-center justify-center ">
    <div class="flex border-2 border-gray-200 rounded">
        <input v-model="searchWord" type="text" class="px-4 py-2 w-80 text-black" placeholder="Search...">
        <button v-on:click="search()" class="px-4 text-white bg-gray-600 border-l ">
            Search
        </button>
    </div>
</div>
<table class="table">
    <thead class="bg-black">
      <tr>
        <th>#</th>
        <th>First</th>
        <th>Last</th>
        <th>Handle</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th scope="row">1</th>
        <td>Mark</td>
        <td>Otto</td>
        <td>@mdo</td>
      </tr>
    </tbody>
  </table>  
    <!-- <div>
        <table>
            <thead>
                <tr>
                    <td>Name</td>
                    <td>Username</td>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>Abir</td>
                    <td>abir</td>
                </tr>
            </tbody>
        </table>
    </div> -->
    <!-- <table class="table-auto">
    <thead class="text-black">
        <tr>
        <th>{{searchData.items}}</th>
        <th>Artist</th>
        <th>Year</th>
        </tr>
    </thead>
    <tbody>
        <tr class="text-black">
        <td>The Sliding Mr. Bones (Next Stop, Pottersville)</td>
        <td>Malcolm Lockyer</td>
        <td>1961</td>
        </tr>
        <tr class="text-black">
        <td>Witchy Woman</td>
        <td>The Eagles</td>
        <td>1972</td>
        </tr>
        <tr class="text-black">
        <td>Shining Star</td>
        <td>Earth, Wind, and Fire</td>
        <td>1975</td>
        </tr>
    </tbody>
    </table> -->
</div>
</template>

<script>
export default {
    data () {
        return {
           searchWord : '',
           searchData: []
        }
    },
    methods: {
        search (){ 
            fetch(`https://api.github.com/search/users?q=${this.searchWord}`, { method: 'GET'})
            .then(response => response.json()).then( function (data) {
                console.log(data.items[0].id);
                let searchData = data.items;
                console.log(searchData)
                // let searchData = data.items;
                // console.log();
                // Now we need to bind this data to our table element to show all the results
            })
            this.searchData.forEach(function(items, index)  {
                console.log(items, index)
                });
            }
        }
}
</script>