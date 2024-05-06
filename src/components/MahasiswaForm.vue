<template>
  <v-container>
    <v-row>
      <v-text-field label="NPM" variant="outlined" v-model="mhs.npm"></v-text-field>
    </v-row>
    <v-row>
      <v-text-field label="Nama" v-model="mhs.nama" variant="outlined"></v-text-field>
    </v-row>
    <v-row>
      <v-text-field label="IPK" v-model="mhs.ipk" variant="outlined"></v-text-field>
    </v-row>
    <v-row>
      <v-btn color="blue" @click="submitMahasiswa">Submit</v-btn>
    </v-row>
  </v-container>
</template>
<script lang="ts">
import { Mahasiswa } from '../model/Mahasiswa'
export default {
  data() {
    return {
      mhs: new Mahasiswa('', '', '')
    }
  },
  methods: {
    submitMahasiswa() {
      if (parseFloat(this.mhs.ipk) <= 4) {
        alert('Data Mahasiswa ' + this.mhs.nama + ' berhasil disimpan')
        this.mhs = new Mahasiswa('', '', '0')
      } else {
        alert('IPK tidak boleh melebihi 4')
      }
    }
  }
}
</script>
