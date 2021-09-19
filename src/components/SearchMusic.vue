<template>
  <div>
    <div class="searching">
      <input
        type="text"
        v-model.lazy="userSearch"
        placeholder="Masukkan lagu"
        @keyup.enter="searching()"
      />
      <input type="submit" @click.enter="searching()" />
      <br /><br />
    </div>

    <!-- <div v-for="music in musics" :key="music.id">
      <img :src="music.album.cover" width="75px" />
      <span class="title">{{ music.title }}</span>
      <br />
      <span class="artist">{{ music.artist.name }}</span>
    </div> -->
    <div class="container">
      <ul>
        <li v-for="music in musics" :key="music.id">
          <img :src="music.album.cover" width="75px" />
          <span class="title" :title="music.title_short">{{
            music.title_short
          }}</span>
          <br />
          <span class="artist">{{ music.artist.name }}</span>
          <br />
          <span class="album" :title="music.album.title">{{
            music.album.title
          }}</span>
        </li>
      </ul>
    </div>

    <!-- <table>
      <tr v-for="music in musics" :key="music.id">
        <td><img :src="music.album.cover" width="75px" /></td>
        <td>
          <span class="title">{{ music.title }}</span>
          <br />
          <span class="artist">{{ music.artist.name }}</span>
        </td>
      </tr>
    </table> -->
    <!-- <ul>
      <li v-for="music in musics" :key="music.id">
        {{ music.title }}
      </li>
    </ul> -->
  </div>
</template>
<script>
const axios = require("axios");
export default {
  name: "SearchMusic",
  data() {
    return {
      userSearch: "",
      musics: [],
    };
  },
  methods: {
    searching() {
      const config = {
        url: ` http://localhost:8080/search?q=${this.userSearch}`,
        method: "GET",
        headers: {
          "Access-Control-Allow-Origin":
            "X-Requested-With, Content-Type, Authorization, Origin, Accept, Accept-Encoding",
          "Content-Type": "application/json",
          "Access-Control-Allow-Credentials": "true",
          "Access-Control-Allow-Methods": "POST, GET, OPTIONS, DELETE, PUT",
        },
      };
      axios(config)
        .then((response) => {
          this.musics = response.data.data;
          console.log(response.data.data);
          console.log("berhasil");
        })
        .catch((error) => {
          console.log("gagal");
          throw error;
        });
    },
  },
};
</script>
<style scoped>
.title {
  font-weight: bold;
}
.artist {
  font-weight: lighter;
}
.album {
  font-size: 15px;
}
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
li {
  float: left;
  padding: 10px;
  margin: 10px;
  width: 250px;
  border: 2px solid green;
  border-radius: 10px;
}
img {
  float: left;
  padding-right: 10px;
}
span {
  float: left;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 150px;
}
#container {
  display: inline-flex;
  flex-direction: row wrap;
  justify-content: space-around;
}
#searching {
  display: block;
  background-color: aliceblue;
}
</style>
