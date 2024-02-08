<template>
    <div class="q-pa-lg" style="max-width: 500px; margin: 0 auto;">
        <q-form
        @submit="onSubmit"
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
      Make: '',
      Model: '',
      Trim: '',
      MinYear: '',
      MaxYear: '',
      City: '',
      State: '',
      Lat: '',
      Long: '',
      Radius: ''
    };
  },
    mounted() {
    document.body.style.backgroundColor = '#EEEEEE';
  },
  methods: {

    runTestFunction() {
            // Make an HTTP request to trigger the desired functionality in index.js
            axios.get('http://localhost:3000/run-test')
                .then(response => {
                    console.log(response.data); // Log the response from the server
                    // Handle the response as needed
                })
                .catch(error => {
                    console.error('Error:', error); // Log any errors
                    // Handle errors as needed
                });
        }



    /*onSubmit() {
      const formData = {
        make: this.Make,
        model: this.Model,
        trim: this.Trim,
        minYear: this.MinYear,
        maxYear: this.MaxYear,
        city: this.City,
        state: this.State,
        lat: this.Lat,
        long: this.Long,
        radius: this.Radius
      };

    const apiUrl = 'https://auto.dev/api/listings';

    const apiKey = 'ZrQEPSkKbWF0dGtudWRzZW4xMEBnbWFpbC5jb20=';

    const apiParams = {
        apikey: apiKey,
        year_min: formData.minYear,
        year_max: formData.maxYear,
        make: formData.make,
        city: formData.city,
        state: formData.state,
        trim: formData.trim,
        model: formData.model,
        latitude: formData.lat,
        longitude: formData.long,
        radius: formData.radius,
    };

    axios.get(apiUrl, { params: apiParams })
    .then(response => {
        const record = response.data.records;
        const recordSize = record.length;

        for (var i=0; i < recordSize; i++) {
            console.log("");
            console.log(record[i].city);
            console.log(record[i].year);
            console.log(record[i].make);
            console.log(record[i].model);
            console.log(record[i].trim);
            //result1 = test();
            //console.log(result1);
        }
    })
    .catch(error => {
        console.error(error.message);
    });
    }*/
  }
}
</script>
    
<style scoped>
    
</style>