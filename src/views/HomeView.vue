<template >
  <div>
    <h1>Все новости</h1>
    <div class="pare">
      <div class="eleme" v-for="item in posts" :key="item.id">
        <h1 class="num">{{ item.id }}</h1>
        <div class="child">
          <div class="tite" @click="e => e.target.classList.toggle('active')">{{ item.title }}</div>
          <div class="userId"> id автора: {{ item.userId }}</div>
          <div class="body">{{ item.body }}</div>
        </div>
        <DialogVue @updatePosts="updatePosts" :posts="posts" :id="item.id" />
      </div>
    </div>

  </div>

</template>

<script>
import axios from "axios";
import DialogVue from "@/components/Dialog.vue";
export default {
  name: 'Home',
  components: {
    DialogVue,
  },
  created() {
    this.getPosts()
  },
  data() {
    return {
      posts: [],
      error: ''
    }
  },
  methods: {
    getPosts() {
      axios.get("https://jsonplaceholder.typicode.com/posts").then((res) => {
        console.log(res.data);
        this.posts = res.data;
      }).catch((erro) => {
        console.log(erro);
        this.error = "There is error"
      })
    },
    updatePosts(res) {
      this.posts = res;
    }
  },
}
</script>
<style>
.active+div+div {
  display: block !important;
}

.active {
  color: blue;
}

.pare {
  background-color: white;
  padding: 25px;
  border-radius: 5px;
  margin-top: 30px;
}

.num {
  color: rgb(147, 141, 141);
  font-weight: 600;
  font-size: 50px;
}

.userId {
  color: #aeaaaa;
}

.eleme {
  cursor: pointer;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  flex-direction: row;
  gap: 50px;
  padding: 30px;

  position: relative;
}

.eleme::before {
  width: 87%;
  content: "";
  left: 34px;
  border: 1px solid #888585;
  position: absolute;
  top: 104%;
}

.body {
  width: 75%;
  display: none;
}

.child {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  flex-direction: column;
  width: calc(75%);
}

.tite {
  font-weight: bolder;
  font-size: 25px;
}

button {
  color: red !important;
}

.row {
  display: inline-flex !important;
  margin: 0 !important;
}

.v-btn:not(.v-btn--round).v-size--default {
  height: fit-content !important;
  min-width: none !important;
  padding: 0 !important;
}

.theme--light.v-btn.v-btn--has-bg {
  background: none !important;
}
</style>