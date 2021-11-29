<template>
  <div>
    <v-text-field
      v-model="letter"
      solo
      label="Search"
    />
    <v-row justify="center" align="center">
      <v-col class="pa-0">
        <v-list v-for="(contact, key) in filteredContacts"
                :key="`${contact} - ${key}`"
                class="py-0"
        >
          <v-list-item
            v-if="!checkLetter(key)"
            dense
            disabled
            class="grey lighten-4"
          >
            <v-list-item-content>
              <v-list-item-title>
                {{ contact.name.last.charAt(0) }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item
            class="my-1"
            @click="selectedContact = contact; dialog = true"
          >
            <v-container>
              <v-row justify="space-around">
                <v-list-item-content>
                  <v-list-item-title>
                    {{ contact.name.title }}.{{ contact.name.last }} {{ contact.name.first }}
                  </v-list-item-title>
                </v-list-item-content>
                <v-list-item-avatar>
                  <v-img :src="contact.picture.large"></v-img>
                </v-list-item-avatar>
              </v-row>
            </v-container>
          </v-list-item>
        </v-list>
      </v-col>
    </v-row>
    <v-dialog
      v-model="dialog"
      fullscreen
      hide-overlay
      transition="dialog-bottom-transition"
    >
      <contact-card
        :contact="selectedContact"
        @close="dialog = false"
      />
    </v-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      contacts: [],
      selectedContact: {},
      info: {},
      letter: '',
      dialog: false
    }
  },
  created() {
    this.getContacts().then(() => {
      this.contacts.sort(this.alphabeticalSort)
    })
  },
  computed: {
    filteredContacts() {
      return this.contacts.filter((contact) => {
        return contact.name.last.toLowerCase().startsWith(this.letter.toLowerCase())
      })
    }
  },
  methods: {
    async getContacts() {
      await this.$axios.get(`/?results=30`).then((res) => {
        this.contacts = res.data.results
        this.info = res.data.info
      })
    },
    alphabeticalSort(a, b) {
      if (a.name.last < b.name.last) return -1;
      if (a.name.last > b.name.last) return 1;
      else return 0;
    },
    checkLetter(index) {
      if (index !== 0) {
        return this.filteredContacts[index].name.last.charAt(0) === this.filteredContacts[index - 1].name.last.charAt(0)
      }
      return false
    }
  }
}
</script>
