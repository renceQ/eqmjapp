<template>
    <div style="margin-right: 500px;">
      <div>
        <br>
        <h4 style="margin-left:580px">Forgot Password</h4>
        <v-sheet>
          <v-form @submit.prevent="submitForm">
            <br>
            <v-text-field v-model="email" label="Email Address" type="email" outlined dense required></v-text-field>
            <v-btn type="submit" block class="mt-2" color="#000000">Send Password Reset Link</v-btn>
          </v-form>
        </v-sheet>
      </div>
  
      <!-- Modal -->
      <v-dialog v-model="showModal" max-width="400">
        <v-card>
          <v-card-title class="headline">Modal Title</v-card-title>
          <v-card-text>
            Sandali naman dipa tapos!
          </v-card-text>
          <v-card-actions>
            <v-btn color="primary" @click="closeModal">Close</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
      <!-- End of Modal -->
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        email: '',
        showModal: false
      };
    },
    methods: {
      submitForm() {
        // Perform actions when the form is submitted
        // For demo purposes, just open the modal
        this.showModal = true;
      },
      closeModal() {
        this.showModal = false;
      }
    }
  };
  </script>
  