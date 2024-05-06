<template>
  <v-navigation-drawer>
    <v-list>
      <v-list-item
        prepend-avatar="WhatsApp Image 2024-05-04 at 11.49.13.jpeg"
        subtitle="auliaku655@gmailcom"
        title="Aulia Hndy"
      ></v-list-item>
    </v-list>

    <v-divider></v-divider>

    <v-list density="compact" nav>
      <v-list-item prepend-icon="mdi-folder" title="Home" :to="'/home'"></v-list-item>
      <v-list-item
        prepend-icon="mdi-account-multiple"
        title="Dosen"
        :to="'/dosen-entry'"
      ></v-list-item>
      <v-list-item prepend-icon="mdi-star" title="Mahasiwa" :to="'/mahasiswa-entry'"></v-list-item>
      <v-list-item prepend-icon="mdi-star" title="Ruangan" :to="'/ruangan-entry'"></v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>
