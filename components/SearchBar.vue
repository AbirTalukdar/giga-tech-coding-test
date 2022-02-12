<template>
<div class="mt-2">
<div class="relative flex items-center justify-center ">
    <h2>Search By User</h2>
    <div class="flex border-2 border-gray-200 rounded">
        <input v-model="searchWord" type="text" class="px-4 py-2 w-80 text-black" placeholder="Search...">
        <button v-on:click="search()" class="px-4 text-white bg-gray-600 border-l ">
            Search
        </button>
    </div>
</div>
    <div>
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
        search (){
            console.log(this.searchWord)
            fetch(`https://api.github.com/search/users?q=${this.searchWord}`, {
                method: 'GET'
            }).then(response => response.json()).then( function (data) {
                console.log(data);
                // Now we need to bind this data to our table element to show all the results
            })
        }
    }
}

</script>