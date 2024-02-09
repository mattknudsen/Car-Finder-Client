<template>
    <div class="q-pa-lg" style="max-width: 500px; margin: 0 auto;">
        <q-form
        @submit="carSearch"
        @reset="onReset"
        class="q-gutter-md"
        >
            <h3>Car Search</h3>
            <q-input
                filled
                v-model="Make"
                label="Make"
            />

            <q-input
                filled
                v-model="Model"
                label="Model"
            />

            <q-input
                filled
                v-model="Trim"
                label="Trim"
            />

            <q-input
                filled
                v-model="MinYear"
                label="Minimum Year"
            />

            <q-input
                filled
                v-model="MaxYear"
                label="Maximum Year"
            />

            <q-input
                filled
                v-model="City"
                label="City"
            />

            <q-input
                filled
                v-model="State"
                label="State"
            />

            <q-input
                filled
                v-model="Lat"
                label="Latitude"
            />

            <q-input
                filled
                v-model="Long"
                label="Longitude"
            />

            <q-input
                filled
                v-model="Radius"
                label="Radius"
            />

        <div>
            <q-btn label="Search" type="submit" color="primary"/>
            <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
            <q-btn label="Run Test Function" color="primary" @click="runTestFunction" />
        </div>
        </q-form>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'HomePage',
    data() {
    return {
        Make: null,
        Model: null,
        Trim: null,
        MinYear: null,
        MaxYear: null,
        City: null,
        State: null,
        Lat: null,
        Long: null,
        Radius: null
    };
  },
    mounted() {
    document.body.style.backgroundColor = '#EEEEEE';
  },
  methods: {

    runTestFunction() {
            // Make an HTTP request to trigger the desired functionality in index.js
            axios.get('http://10.0.91.35:3000/run-test')
                .then(response => {
                    console.log(response.data); // Log the response from the server
                    // Handle the response as needed
                })
                .catch(error => {
                    console.error('Error:', error); // Log any errors
                    // Handle errors as needed
                });
    },

    carSearch() {
        // Prepare the data object to send to the server
      const searchData = {
        Make: this.Make,
        Model: this.Model,
        Trim: this.Trim,
        MinYear: this.MinYear,
        MaxYear: this.MaxYear,
        City: this.City,
        State: this.State,
        Lat: this.Lat,
        Long: this.Long,
        Radius: this.Radius
      };

      // Make a POST request to send the search data to the server
      axios.post('http://10.0.91.35:3000/car-search', searchData)
        .then(response => {
          // Handle the response from the server as needed
          console.log(response.data);
        })
        .catch(error => {
            console.log(searchData);
          // Handle errors
          console.error('Error:', error);
        });
    },

    onReset() {
      // Clear input fields on reset
      this.Make = '';
      this.Model = '';
      this.Trim = '';
      this.MinYear = '';
      this.MaxYear = '';
      this.City = '';
      this.State = '';
      this.Lat = '';
      this.Long = '';
      this.Radius = '';
    }

  }
}
</script>
    
<style scoped>
    
</style>