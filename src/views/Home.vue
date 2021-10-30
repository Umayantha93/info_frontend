<template>
    <div class="container">
           <input
              class="bg-gray-800 m-4 rounded px-2 py-1 border border-purple-200"
              type="text"
              v-model="search"
            />
            <input class="bg-gray-800 p-2 rounded shadow-md border" type="submit" @click.prevent="doSearch()"
            value="search"/>

        <h3 class="p-3 text-center">Clients</h3>
        <table class="table table-striped table-bordered">
            <thead>
                <tr>
                    <th scope="col">#</th>
                    <th scope="col">Id Number</th>
                    <th scope="col">Name</th>
                    <th scope="col">Birth Date</th>
                    <th scope="col">Contact Number</th>
                    <th scope="col">Age</th>
                    <th scope="col">Address</th>
                    <th scope="col">Religion</th>
                    <th scope="col">Nationality</th>
                    <th scope="col">Image</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user in users" :key="user.id">
                    <td scope="row">{{user.id}}</td>
                    <td scope="row">{{user.id_number}}</td>
                    <td scope="row">{{user.person_name}}</td>
                    <td scope="row">{{user.date_of_birth}}</td>
                    <td scope="row">{{user.contact_number}}</td>
                    <td scope="row">{{user.age}}</td>
                    <td scope="row">{{user.address}}</td>
                    <td scope="row">{{user.religion}}</td>
                    <td scope="row">{{user.nationality}}</td>
                    <td scope="row"><img :src= "'{{ url('/') }}/' + user.image_path" width="150px"></td>
                </tr>
            </tbody>
        </table>
    </div>    
</template>

<script>
// @ is an alias to /src
import axios from 'axios';

export default {
  name: 'Home',

         data() {
            return {
              users: [],
              search: "",
              params: []
            }
        },
        watch: {
            search(value) {
                this.doSearch(value);
            }
        },
        methods: {
            getUser(){
                axios.get('http://127.0.0.1:8000/api/get')
                     .then((response)=>{
                       this.users = response.data
                       console.log(this.users);
                     })
            },
            doSearch(value) {
                console.log(value);
                if(value != "" ){
                axios.get('http://127.0.0.1:8000/api/search/'+value)
                .then((response) => this.users = response.data)
                .catch(e => console.log(e));
                }
            }
        },
        created() {
            this.getUser()
        },
}
</script>
