<template>
  <div class="wrapper">
    <div class="section page-header header-filter" :style="headerStyle">
      <div class="container">
        <div class="md-layout">
          <div
            class="md-layout-item md-size-80 md-small-size-66 md-xsmall-size-100 md-medium-size-40 mx-auto"
          >
            <login-card header-color="green">
              <h4 slot="title" class="card-title">Summary</h4>
              <h5
                slot="inputs"
              >Lorem ipsum dolor sit, amet consectetur adipisicing elit. Ex, culpa consequatur. Quis officiis, voluptates eum rerum dolorem alias, ullam aspernatur tempore maxime quos voluptate perspiciatis vel, porro non laboriosam! Consequuntur.</h5>
              <div class="comment-area" slot="inputs">
                <md-field maxlength="5">
                  <label>Write a nice reply or go home...</label>
                  <md-textarea v-model="aboutme"></md-textarea>
                </md-field>
                <div class="comment-footer">
                  <md-button href="javascript:void(0)" class="md-success">
                    <md-icon>reply</md-icon>Reply
                  </md-button>
                </div>
                <div class="comment">
                  <div class="comment-body">
                    <h4 class="comment-heading">
                      Tina Andrew
                      <small>· 7 minutes ago</small>
                    </h4>

                    <p>
                      Chance too good. God level bars. I'm so proud of
                      @LifeOfDesiigner #1 song in the country. Panda! Don't be
                      scared of the truth because we need to restart the human
                      foundation in truth I stand with the most humility. We are so
                      blessed!
                    </p>
                  </div>
                </div>
                <div class="comment">
                  <div class="comment-body">
                    <h4 class="comment-heading">
                      Tina Andrew
                      <small>· 7 minutes ago</small>
                    </h4>

                    <p>
                      Chance too good. God level bars. I'm so proud of
                      @LifeOfDesiigner #1 song in the country. Panda! Don't be
                      scared of the truth because we need to restart the human
                      foundation in truth I stand with the most humility. We are so
                      blessed!
                    </p>
                  </div>
                </div>
                <div class="comment">
                  <div class="comment-body">
                    <h4 class="comment-heading">
                      Tina Andrew
                      <small>· 7 minutes ago</small>
                    </h4>

                    <p>
                      Chance too good. God level bars. I'm so proud of
                      @LifeOfDesiigner #1 song in the country. Panda! Don't be
                      scared of the truth because we need to restart the human
                      foundation in truth I stand with the most humility. We are so
                      blessed!
                    </p>
                  </div>
                </div>
                <pagination
                  class="justify-content-center"
                  type="success"
                  v-model="defaultPagination"
                  :page-count="5"
                ></pagination>
              </div>
              <md-button slot="footer" class="md-success">Close ticket</md-button>
            </login-card>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { LoginCard, FileUpload, Pagination } from "@/components";
import Mixins from "@/plugins/basicMixins";

export default {
  mixins: [Mixins.HeaderImage],
  components: {
    LoginCard,
    FileUpload,
    Pagination
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
      defaultPagination: 3,
      Summary: "",
      image: require("@/assets/img/profile_city.jpg"),
      firstname: "",
      email: null,
      password: null
    };
  }
};
</script>

<style lang="css"></style>