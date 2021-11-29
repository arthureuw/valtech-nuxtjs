<template>
  <v-card>
    <v-toolbar
      dark
      color="primary"
    >
      <v-toolbar-title>{{ contact.name.title }}.{{ contact.name.first }} {{ contact.name.last }}</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn
          icon
          dark
          @click="close()"
        >
          <v-icon>mdi-close</v-icon>
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <v-container>
      <v-card-title
        class="grey lighten-3 pa-0"
      >
        <v-img max-height="200" src="https://picsum.photos/2000/200/?blur=4&grayscale">
        <v-avatar
          size="100"
        >
          <img
            :src="contact.picture.large"
            :alt="contact.name.first"
          >
        </v-avatar>
        <p class="ml-3 text-h4">{{ contact.name.first }} {{ contact.name.last }}</p>
        </v-img>
      </v-card-title>
      <br>
      <v-card-text>
        <v-row
          align="center"
          class="grey lighten-3 rounded"
        >
          <v-col cols="2" lg="1" md="2" sm="2" xs="4">
            <v-btn
              icon
            >
              <v-icon>
                mdi-phone-dial
              </v-icon>
            </v-btn>
          </v-col>
          <v-col>
            <div class="subtitle-1">Number</div>
            <div class="blue--text">{{ contact.phone }}</div>
          </v-col>
          <v-spacer></v-spacer>
          <v-col cols="2" lg="1" md="2" sm="2" xs="4">
            <v-btn
              icon
            >
              <v-icon>
                mdi-phone
              </v-icon>
            </v-btn>
          </v-col>
        </v-row>
        <v-row
          align="center"
          class="grey lighten-3 rounded mt-6"
        >
          <v-col cols="2" lg="1" md="2" sm="2" xs="4">
            <v-btn
              icon
            >
              <v-icon>
                mdi-at
              </v-icon>
            </v-btn>
          </v-col>
          <v-col>
            <div class="subtitle-1">Email</div>
            <div class="blue--text">{{ contact.email }}</div>
          </v-col>
        </v-row>
        <v-row
          align="center"
          class="grey lighten-3 rounded mt-6"
        >
          <v-col cols="2" lg="1" md="2">
            <v-btn
              icon
            >
              <v-icon>
                mdi-map-marker
              </v-icon>
            </v-btn>
          </v-col>
          <v-col cols="7">
            <div class="subtitle-1">Location</div>
            <div class="blue--text">{{ contact.location.street.number }} {{ contact.location.street.name }} <br>
              {{ contact.location.postcode }} {{ contact.location.city }}
            </div>
          </v-col>
          <v-spacer></v-spacer>
          <v-col
            cols="2"
            class="pa-0"
          >
            <v-img
              max-height="150"
              src="https://i.postimg.cc/MKVY2LMj/Capture-d-e-cran-2021-11-29-a-15-44-49.png"
            ></v-img>
          </v-col>
        </v-row>
        <v-row
          align="center"
          class="grey lighten-3 rounded mt-6"
        >
          <v-col cols="2" lg="1" md="2">
            <v-btn
              icon
            >
              <v-icon>
                mdi-cake-variant
              </v-icon>
            </v-btn>
          </v-col>
          <v-col>
            <div class="subtitle-1">Anniversary</div>
            <div class="blue--text">{{ contact.registered.date.toUTCString }}</div>
          </v-col>
        </v-row>
      </v-card-text>
    </v-container>
  </v-card>
</template>

<script>
export default {
  props: {
    contact: Object
  },
  data() {
    return {}
  },
  methods: {
    close() {
      this.$emit('close')
    }
  }
}
</script>
