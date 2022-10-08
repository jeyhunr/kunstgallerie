<template>
  <div class="main-card">
    <div class="card-content">
      <div class="card-info">
        <div class="card-left">
          <img :src=post.url alt="" />
        </div>
        <div class="card-right">
          <h1>{{ post.title }}</h1>
          <p>{{ post.id }}</p>
        </div>
      </div>
      <div class="card-link">
        <a :href=post.thumbnailUrl target="_blank">Zum Bild</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: { post: { required: true, type: Object } },
  name: "main-card",
};
</script>

<style>
.main-card {
  padding: 12px;
  position: relative;
  width: 261.5px;
  height: 111px;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 4px;
  transition: 0.2s;
}
.main-card:hover {
  box-shadow: 0 1rem 3rem rgba(0, 0, 0, 0.175);
  transition: 0.2s;
}
.card-content {
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 100%;
  height: 100%;
}
.card-info {
  display: flex;
  gap: 12px;
  width: 100%;
  height: 60px;
}
.card-left {
  width: 80px;
  height: 60px;
}
.card-left > img {
  border-radius: 8px;
  width: 80px;
  height: 60px;
}
.card-right {
  display: flex;
  flex-direction: column;
  gap: 4px;
  width: 100%;
  height: 100%;
}
.card-right > h1 {
  font-size: 17.778px;
  line-height: 115%;
  margin-top: 12px;
  margin-bottom: 0px;
  font-weight: 600;
}
.card-right > p {
  margin: 0;
  font-weight: 400;
  font-size: 14.047px;
  line-height: 115%;
  color: #767676;
}
.card-link {
  position: absolute;
  bottom: 0;
}
.card-link > a {
  font-style: normal;
  font-weight: 600;
  font-size: 14px;
  line-height: 115%;
  text-decoration-line: underline;
  color: #000000;
}
</style>
