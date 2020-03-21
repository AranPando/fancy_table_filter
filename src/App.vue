<template>
  <v-app>
    <AppBar />

    <v-content>
      <h1 class="text-center mt-5 mb-5">Fnacy Table Filter</h1>

      <v-container>
        <v-row>
            <!-- Input -->
          <v-col cols="12" sm="6" class="mx-auto">
            <v-text-field
              v-model="minVal"
              label="Min value"
              outlined
              clearable
              type='number'
            ></v-text-field>
          </v-col>

          <!-- slider -->
          <v-col cols="12" class="mx-auto">
            <v-slider
              v-model="minVal"
              thumb-label
              :max="MaxValue"
              :min="MinValue"
            />
          </v-col>

            <!-- table -->
          <v-col cols="12">
            <ul>
              <v-data-table 
                :headers="headers" 
                :items="GetValues" 
                item-key="name" 
                class="elevation-2"
                outlined
              />
            </ul>
          </v-col>

        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import AppBar from './components/AppBar'

export default {
  name: 'App',

  components: {
    AppBar,
  },

  computed: {
    GetValues() {
      return this.values.filter(row => row.value >= this.minVal)
    },
    MaxValue() {
      return Math.max.apply(Math, this.values.map(function(row) { return row.value; }))
    },
    MinValue() {
      return Math.min.apply(Math, this.values.map(function(row) { return row.value; }))
    }
  },

  data () {
    return {
      minVal: null,
      headers: [
        {
          text: 'Email',
          align: 'start',
          sortable: false,
          value: 'email',
        },
        { text: 'Value', value: 'value' },
      ],
      values: [
        {
          email: "example1@gmail.com",
          value: 1000,
        },
        {
          email: "example2@gmail.com",
          value: 2000,
        },
        {
          email: "example3@gmail.com",
          value: 3000,
        },
        {
          email: "example4@gmail.com",
          value: 4000,
        },
        {
          email: "example5@gmail.com",
          value: 5000,
        },
        {
          email: "example6@gmail.com",
          value: 6000,
        },
        {
          email: "example7@gmail.com",
          value: 7000,
        },
        {
          email: "example8@gmail.com",
          value: 8000,
        },
        {
          email: "example9@gmail.com",
          value: 9000,
        },
        {
          email: "example10@gmail.com",
          value: 10000,
        },
      ]
    }
  },
};
</script>
