<template>
  <v-container style="width: 700px; margin-left: 80px">
    <v-card class="profile-card" elevation="10" style="max-width: 600px">
      <!-- TITLE START -->
      <v-row justify="center" class="mt-3 mb-3">
        <v-card-title class="text-h6 text-md-h5 text-lg-h4">
          <v-btn variant="text"> ENTRY DATA MAHASISWA </v-btn>
        </v-card-title>
      </v-row>
      <!-- TITLE END -->

      <!-- FIELD START -->
      <v-row class="ml-2 mr-2">
        <v-text-field
          label="NPM"
          v-model="mahasiswa.npm"
          variant="underlined"
          :rules="[rules.required]"
        ></v-text-field>
      </v-row>
      <v-row class="ml-2 mr-2">
        <v-text-field
          label="NAMA"
          v-model="mahasiswa.nama"
          variant="underlined"
          :rules="[rules.required]"
        ></v-text-field>
      </v-row>
      <v-row class="ml-2 mr-2">
        <v-text-field
          label="IPK"
          v-model="mahasiswa.ipk"
          variant="underlined"
          :rules="[rules.required, rules.validIpk]"
        ></v-text-field>
      </v-row>
      <!-- FIELD END -->

      <!-- SUBMIT -->
      <v-row justify="center" class="mt-3 mb-3">
        <v-btn rounded="xl" size="small" color="surface-variant" @click="submitMahasiswa">
          SIMPAN
        </v-btn>
      </v-row>
      <!-- SUBMIT END -->

      <!-- DIALOG START -->
      <v-dialog v-model="dialog" max-width="500" rounded="pill">
        <v-card>
          <v-card-title class="headline">Data Berhasil Disimpan</v-card-title>
          <v-card-actions>
            <v-btn color="primary" text @click="dialog = false">OKE</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
      <!-- DIALOG END -->
    </v-card>
  </v-container>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { Mahasiswa } from '@/model/Mahasiswa'

export default defineComponent({
  data() {
    return {
      mahasiswa: new Mahasiswa('', '', ''),
      showRules: false,
      dialog: false
    }
  },
  computed: {
    rules() {
      return {
        required: (value: string) => !!value || 'Masukkan data',
        validIpk: (value: string) => {
          const ipk = parseFloat(value)
          if (isNaN(ipk) || ipk < 0 || ipk > 4) {
            return 'IPK harus antara 0 sampai 4'
          }
          return true
        }
      }
    }
  },
  methods: {
    submitMahasiswa() {
      if (!this.mahasiswa.npm || !this.mahasiswa.nama || !this.mahasiswa.ipk) {
        this.showRules = true
      } else {
        this.dialog = true
        this.mahasiswa = new Mahasiswa('', '', '')
        this.showRules = false
      }
    }
  }
})
</script>
