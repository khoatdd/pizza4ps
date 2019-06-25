<template>
  <div class="wrapper">
    <div class="section page-header header-filter" :style="headerStyle">
      <div class="container">
        <div class="md-layout">
          <div
            class="md-layout-item md-size-50 md-small-size-66 md-xsmall-size-100 md-medium-size-40 mx-auto"
          >
            <form enctype="multipart/form-data">
              <login-card header-color="green">
                <h4 slot="title" class="card-title">Store ticket</h4>
                <md-field slot="inputs">
                  <label for="movie">Choose Store (*)</label>
                  <md-select v-model="selectedStore" tname="store" id="store">
                    <md-option
                      :value="store.name"
                      v-for="(store, index) in stores"
                      :item="store"
                      :key="index"
                    >{{ store.name }}</md-option>
                  </md-select>
                </md-field>
                <md-field slot="inputs">
                  <label for="movie">Store Ticket Type (*)</label>
                  <md-select v-model="ticketType" name="ticketType" id="ticketType">
                    <md-option value="POS">POS</md-option>
                    <md-option value="IT Devices">IT Devices</md-option>
                  </md-select>
                </md-field>
                <md-field slot="inputs">
                  <label>Summary (*)</label>
                  <md-input v-model="summary"></md-input>
                </md-field>
                <md-field slot="inputs">
                  <label>Description</label>
                  <md-textarea v-model="description"></md-textarea>
                </md-field>
                
                <file-upload
                  type="input"
                  placeholder="Select file"
                  input-name="fileSimple2"
                  btn-icon="attach_file"
                  with-button
                  slot="inputs"
                  @fileHasChanged="onFileChange($event.target.name, $event.target.files)"
                >
                </file-upload>
                <md-button slot="footer" class="md-success">Submit</md-button>
              </login-card>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { LoginCard, FileUpload } from "@/components";
import Mixins from "@/plugins/basicMixins";
import axios from 'axios';

export default {
  mixins: [Mixins.HeaderImage],
  components: {
    LoginCard,
    FileUpload
  },
  bodyClass: "login-page",
  data() {
    return {
      stores: [
        {
          id: 1,
          name: "HCM-HBT"
        },
        {
          id: 2,
          name: "HCM-VVK"
        },
        {
          id: 3,
          name: "HCM-VVK"
        },
        {
          id: 4,
          name: "HCM-VVK"
        },
        {
          id: 5,
          name: "HCM-VVK"
        }
      ],
      selectedStore: "",
      ticketType: "",
      summary: "",
      description: "",
      image: require("@/assets/img/profile_city.jpg"),
      firstname: "",
      email: null,
      password: null
    };
  },
  methods: {
    upload(formData) {
      axios.post( 'https://gasupport.pizza4ps.com:8888/api4/uploadefile',
        formData,
        {
          headers: {
              'Content-Type': 'multipart/form-data'
          },
          crossdomain: true
        }
      )
      .then(response => (this.fileurl = response))
      .catch(err => {
        console.log(err)
      });
    },
    save(formData) {
      // upload data to the server
      axios.post( 'https://gasupport.pizza4ps.com:8888/api4/uploadefile',
        formData,
        {
          headers: {
              'Content-Type': 'multipart/form-data'
          }
        }
      )
      .then(response => (this.fileurl = response))
      .catch(err => {
        console.log(err)
      });
    },
    onFileChange(fieldName, fileList) {
      console.log("File changed in parent");
      console.log(fileList);
      // handle file changes
      const formData = new FormData();
      if (!fileList.length) return;
      // append the file to FormData
      formData.append(fieldName,fileList[0])
      // save it
      this.save(formData);
    }
  }
};
</script>

<style lang="css"></style>