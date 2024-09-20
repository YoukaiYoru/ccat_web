<template>
  <v-footer color="#1B263B" padless center>
    <v-col cols="3" justify="center" no-gutters>
      <v-row class="d-flex justify-center">
        <v-btn
          v-for="link in links"
          :key="link.id"
          :href="link.url"
          target="_plank"
          rounded
          flat
          title
          icon
          color="transparent"
          class="text-white my-5 mx-1"
        >
          <v-icon size="41px" color="white">{{ link.icon }}</v-icon>
        </v-btn>
      </v-row>
      <v-row
        class="primary lighten-2 py-4 text-center text-white d-flex flex-row justify-center"
        color="white"
        cols="10"
      >
<!-- dialog button -->
        <v-btn
          height="50px"
          width="auto"
          density="deafault"
          prepend-icon="mdi-information"
          variant="tonal"
          rounded="lg"
          elevation="4"
          @click="dialog = true"

        >Escríbenos</v-btn>
<!--Dialog Contact-->

        <v-dialog
        v-model="dialog"
        width="942px"
        height="auto"
        >
          <v-sheet class="d-flex form-bg">
            <v-card class="form-bg w-75 rounded-0 elevation-0"
            height="638px">
              <svg
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 570 870"
                  >
                    <path fill="#1B263B" d="M203.5 409.5 571 0v810.5h-26l-341.5-401Z"/>
                    <path fill="#D9E8F6" d="M0 0h571L203.5 409.5 0 160.5V0Z" />
                    <path fill="#3384BA" d="M203.5 409.5 0 160.5V647l203.5-237.5Z"/>
                    <path fill="#778DA9" d="m0 646.5 203.5-237 341.5 401H0v-164Z"/>
                    <path fill="#D9E8F6" d="M344.5 477V345L286 409.5l58.5 67.5Z"/>
                  </svg>
            </v-card>
            <v-col
              cols="12"
              sm="12"
              md="6">
            <v-form>
              <v-col>
              <h2
              class="ma-2"
              >Contáctanos</h2>
              <v-row
              class="pa-1">                
                <v-col>
                  <v-text-field
                    v-model="name"
                    label="Nombre"
                    bg-color="grey-lighten-2"
                    :rules="nameRules"
                    class="mt-1 mb-1"
                  >
                  </v-text-field>
                </v-col>
                <v-col>
                  <v-text-field
                    v-model="lastName"
                    label="Apellido"
                    bg-color="grey-lighten-2"
                    class="mt-1 mb-3"
                  >
                  </v-text-field>
                </v-col>
              </v-row>
            <v-col
              class="pa-1"
            >
            <v-text-field
              class="mb-3"
              v-model="email"
              label="Correo"
              bg-color="grey-lighten-2"
              :rules="emailRules"
              >
            </v-text-field>
            <v-text-field
              class=" mb-3"
              v-model="phone"
              label="Celular"
              bg-color="grey-lighten-2"
            ></v-text-field>
            <v-textarea
              class="mb-3"
              v-model="message"
              label="Mensaje"
              bg-color="grey-lighten-2">
            </v-textarea>
            </v-col>
            <v-row
            class="d-flex-inline justify-end"
            >
              <v-btn
              class="ma-5"
              >Enviar</v-btn>
              <v-btn
              class="ma-5"
              @click="dialog=false"
              >Cancelar</v-btn>
            </v-row>
            </v-col>
            </v-form>
            </v-col>
          </v-sheet>
        </v-dialog>





      </v-row>
    </v-col>

    <v-row justify="center" class="text-white d-flex">
      <v-card
        v-for="contact in contacts"
        :key="contact.id"
        flat
        color="transparent"
        max-width="60%"
        class="footer-contact my-5 mx-1 text-white"
        text
      >
        <v-card-text class="text-white" color="white">
          <v-icon> {{ contact.icon }} </v-icon>
          {{ contact.description }}
        </v-card-text>
      </v-card>
    </v-row>
  </v-footer>
</template>

<style scoped>
h2{
  color: #D9E8F6;
}
.form-bg{
  background-color:#1B263B;
;
}
.title-style{
  color: #D9E8F6;
} 

</style>

<script setup>
import { ref } from "vue";

const links = ref([
  { id: 1, icon: "mdi-youtube", url: "https://www.youtube.com/@CCATFIIS" },
  { id: 2, icon: "mdi-facebook", url: "https://www.facebook.com/ccat.pe/" },
  {
    id: 3,
    icon: "mdi-instagram",
    url: "https://www.instagram.com/ccat.pe/?hl=en",
  },
  {
    id: 4,
    icon: "mdi-linkedin",
    url: "https://www.linkedin.com/company/ccatpe?originalSubdomain=pe",
  },
]);

const contacts = ref([
  {
    id: 1,
    icon: "mdi-map-marker",
    description:
      "Facultad de Ingeniería Industrial y de Sistemas - UNI, Rímac 15333 Lima, Perú",
  },
  { id: 2, icon: "mdi-clock", description: "Lun-Vie 8:30 - 21:00" },
  { id: 3, icon: "mdi-email", description: "ccat.fiis@uni.edu.pe" },
  // { id: 4, icon: 'mdi-phone', description: '(01) 626-2000 anexo 1111' },
  // { id: 5, icon: 'mdi-whatsapp', description: '943 000 000'}
]);

let dialog = ref(false);


//Form-contact-rules
const name = ref('');
const lastName = ref('');
const email = ref('');
const phone = ref('');
const message = ref('');

const nameRules = [
  (value) => {
    if (value) return true;
    return 'Nombre requerido';
  },
  (value) => {
    if (value?.length <= 0) return true;
    return 'Necesario';
  },
];
const emailRules = [
  (value) => {
    if (value) return true;
    return 'Correo necesario.';
  },
  (value) => {
    if (/.+@.+\..+/.test(value)) return true;
    return 'Correo tiene que ser válido.';
  },
];

</script>
