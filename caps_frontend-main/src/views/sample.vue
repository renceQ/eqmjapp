<template>
    <div>
      <input type="file" ref="fileInput" @change="handleFileChange" />
      <div v-if="previewUrl">
        <h4>Preview:</h4>
        <img :src="previewUrl" alt="File Preview" />
      </div>
      <button @click="uploadFile">Upload</button>
    </div>
  </template>
  
  <script>
  import axios from 'axios'
  export default {
    data() {
      return {
        previewUrl: null
      };
    },
    methods: {
      handleFileChange() {
        const fileInput = this.$refs.fileInput;
        const file = fileInput.files[0];
  
        if (file) {
          this.displayFilePreview(file);
        } else {
          this.previewUrl = null;
          console.error('No file selected');
        }
      },
      displayFilePreview(file) {
        const reader = new FileReader();
  
        reader.onload = (event) => {
          this.previewUrl = event.target.result;
        };
  
        reader.readAsDataURL(file);
      },
      uploadFile() {
        const fileInput = this.$refs.fileInput;
        const file = fileInput.files[0];
  
        if (file) {
          this.uploadFileToServer(file);
        } else {
          this.previewUrl = null;
          console.error('No file selected');
        }
      },
      uploadFileToServer(file) {
        const formData = new FormData();
        formData.append('file', file);
  
        // Make a POST request to your API endpoint
        // Adjust the URL and other options based on your API requirements
        axios.post('upload', formData)
          .then(response => {
            console.log('File uploaded successfully', response.data);
          })
          .catch(error => {
            console.error('Error uploading file', error);
          });
      }
    }
  };
  </script>
  