<template>
  <div class="api-page">
    <MainHeader :title="pageTitle" />
    <hr />
    <div v-if="result" class="result">
      <p>
        <b>Es wurde erfolgreich gespeichert</b>
        <br />
        {{ message }}
      </p>
    </div>
    <h1 class="text-center">Einen neuen Beitrag erstellen</h1>
    <Form @myevent="addPost" event="myevent">
      <TextInput
        v-model.trim="apiTitle"
        type="text"
        name="title"
        placeholder="Title"
        label="Title"
        required="required"
      />
      <TextInput
        v-model="apiUrl"
        type="text"
        name="url"
        placeholder="Url"
        label="Url"
        required="required"
      />
      <TextInput
        v-model="apiThumbnailUrl"
        type="text"
        name="thumbnailUrl"
        placeholder="ThumbnailUrl"
        label="ThumbnailUrl"
        required="required"
      />
      <div class="w-100">
        <LinkButton title="Erstellen" />
      </div>
    </Form>

    <hr />
    <CardList
      :posts="fetchedPosts"
      :loadEightPosts="loadEightPosts"
      :loadTwentyPosts="loadTwentyPosts"
      :countOfPosts="countOfPosts"
    />
  </div>
</template>

<script>
import MainHeader from "@/components/headers/main-header.vue";
import Form from "@/components/forms/forms.vue";
import TextInput from "@/components/inputs/TextInput.vue";
import LinkButton from "@/components/buttons/link-button.vue";
import CardList from "@/components/card-lists/main-card-list.vue";
export default {
  components: {
    MainHeader,
    Form,
    TextInput,
    LinkButton,
    CardList,
  },
  data() {
    return {
      pageTitle: "API",
      fetchedPosts: [],
      countOfPosts: 8,
      apiTitle: "",
      apiUrl: "",
      apiThumbnailUrl: "",
      message: "",
      result: false,
    };
  },
  async created() {
    const getPosts = await this.getPosts(this.countOfPosts);
  },
  methods: {
    async loadEightPosts() {
      this.countOfPosts += 8;
      const getPosts = await this.getPosts(this.countOfPosts);
    },
    async loadTwentyPosts() {
      this.countOfPosts += 20;
      const getPosts = await this.getPosts(this.countOfPosts);
    },
    async getPosts(countOfPosts) {
      const api =
        "https://kunstgallerie.herokuapp.com/api/v1/posts/getpost/" +
        this.countOfPosts;
      const response = await fetch(api);
      const posts = await response.json();
      this.fetchedPosts = posts;
    },
    async addPost() {
      const postAPI = "https://kunstgallerie.herokuapp.com/api/v1/posts/insertpost";
      const payload = {
        "title": this.apiTitle,
        "url": this.apiUrl,
        "thumbnailUrl": this.apiThumbnailUrl,
      };
      const requestOptions = {
        method: "POST",
        headers: {
          "Content-Type": "application/x-www-form-urlencoded;charset=UTF-8",
        },
        body: new URLSearchParams(payload),
      };
      console.log(requestOptions);
      const res = await fetch(postAPI, requestOptions);
      const content = await res.json();

      // save the response from api to variable
      this.message = content;

      // fade in alert message
      // fade out the message after 3 seconds
      this.result = true;
      setTimeout(() => (this.result = false), 3000);

      // load again
      const getPosts = await this.getPosts(this.countOfPosts);
    },
  },
};
</script>
<style>
.api-page {
  width: 100%;
}
hr {
  height: 1px;
  border: none;
  width: 100%;
  background: #d9d9d9;
}
.text-center {
  text-align: center;
}
.result {
  text-align: center;
}
.result > p {
  color: green;
  font-size: 20px;
}
</style>
