<template>
  <div class="container py-4">
    <div class="row justify-content-center">
      <div class="col-md-5">
        <div class="card">
          <div class="card-header">Login</div>
          <div class="card-body">
            <form method="post">
              <div class="mb-3">
                <label for="id_number" class="form-label">Id Number</label>
                <input type="text" class="form-control" id="id_number" v-model="id_number">
              </div>
              <div class="mb-3">
                <label for="person_name" class="form-label">Name</label>
                <input type="text" class="form-control" id="person_name" v-model="person_name">
              </div>
              <div class="mb-3">
                <label for="date" class="form-label">Date of Birth</label>
                <input type="date" class="form-control" id="date_of_birth" v-model="date_of_birth">
              </div>
              <div class="mb-3">
                <label for="contact_number" class="form-label">Contact Number</label>
                <input type="text" class="form-control" id="contact_number" v-model="contact_number">
              </div>
              <div class="mb-3">
                <label for="age" class="form-label">Age</label>
                <input type="text" class="form-control" id="age" v-model="age">
              </div>
              <div class="mb-3">
                <label for="address" class="form-label">Address</label>
                <input type="text" class="form-control" id="address" v-model="address">
              </div>
              <div class="mb-3">
                <label for="religion" class="form-label">Select a Religion</label>
              <select class="form-select" aria-label="Default select example" v-model="religion">
                <option selected>Religions</option>
                <option value="buddhist">Buddhist</option>
                <option value="chatholic">Chatholic</option>
                <option value="muslim">Muslim</option>
                <option value="hindu">Hindu</option>
                <option value="other">Other</option>
              </select>
              </div>
              <div class="mb-3">
                <label for="nationality" class="form-label">Nationality</label>
                <input type="text" class="form-control" id="nationality" v-model="nationality">
              </div>
              <div class="mb-3">
                <label for="image" class="form-label">Add Image</label>
                <input type="text" class="form-control" id="image_path" v-model="image_path">
              </div>
              <button type="submit" @click.prevent="saveData" class="btn btn-primary">Submit</button>
            </form>
          </div>  
        </div>
      </div>
    </div>        
  </div>
</template>

<script>
import axios from 'axios'
    export default{
      data(){
        return {
          id_number : '',
          person_name : '',
          date_of_birth : '',
          contact_number : '',
          age : '',
          address : '',
          religion : '',
          nationality : '',
          image_path : ''
        }
      },
      mounted() {
        console.log('component mounted.')
      },
      methods : {
        saveData(){
          axios.post('http://127.0.0.1:8000/api/register',{
          id_number : this.id_number,
          person_name : this.person_name,
          date_of_birth : this.date_of_birth,
          contact_number : this.contact_number,
          age : this.age,
          address : this.address,
          religion : this.religion,
          nationality : this.nationality,
          image_path : this.image_path
          })
          .then(response => console.log(response))
                  .catch(error => {
        alert("entered data is wrong", error)
        this.errored = true
        })
      }
    }
    }
</script>
