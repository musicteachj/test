<template>
  <div>
    <v-container>
      <v-dialog
          v-model="show"
          width="500"
        >
          <v-card>
            <v-card-title
              class="headline grey lighten-2"
              primary-title
            >
              Edit Barcode
            </v-card-title>

            <v-container>
              <v-text-field
              clearable
              v-model="newThing">
            </v-text-field>
            <div id="barcodeContainer">
              <barcode
                :value="newThing">
              </barcode>
            </div>
            </v-container>
            <v-divider></v-divider>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn
                color="primary"
                flat
                @click="show = false"
              >
                I accept
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
    </v-container>
  </div>
</template>

<script>
import VueBarcode from 'vue-barcode';

export default {
  props: ['dPost', 'value'],
  components: {
      'barcode': VueBarcode
    },

  data() {
    return {
      dialog: false,
      newThing: "test"
    }
  },
  methods: {
    openED() {
      
      this.dialog = true;
    }
  },
  computed: {
    show: {
      get () {
        return this.value
      },
      set (value) {
         this.$emit('input', value)
      }
    }
  },
  beforeUpdate() {
    this.newThing = "check";
  }
}
</script>
