<template>
    <div class="error-page">
        <h1>{{ header }}</h1>
        <p>{{ message }}</p>
    </div>
</template>
<script>
export default {
  name: 'Error',
  data() {
    return {
      header: "404",
      message: "Seite nicht gefunden :("
    };
  },
}
</script>
<style>
.error-page {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    color: #6d2091;
    font-size: 2rem;
    width: 100%;
}
.error-page > h1 {
    margin-bottom: 0px;
    animation: jumping 2s linear infinite;
}
.error-page > p {
    margin-top: 0px;
}

/* animations */
@keyframes jumping {
    0% {
        margin-bottom: 0px;
    }
    50% {
        margin-bottom: 15px;
    }
    100% {
        margin-bottom: 0px;
    }
}
</style>