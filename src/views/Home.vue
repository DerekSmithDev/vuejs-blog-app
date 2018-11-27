<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div id="map"></div>
    <!-- blog app -->
<!--     <div class="container">
      
      <div class="row">

        <div v-for="post in posts" class="col-md-4 mb-2">
          <div class="card">
            <img class="card-img-top" v-bind:src="post.image" alt="Card image cap">
            <div class="card-body">
              <h5 class="card-title">{{ post.title }}</h5>
              <p class="card-text">Supplier: {{ post.body }}</p>
              <p class="card-text">Price: {{ post.id }}</p>
              <a v-bind:href="`/#/posts/${post.id}`" class="btn btn-primary">Go somewhere</a>
            </div>
          </div>
        </div>

      </div>  
    </div> -->
  
  </div>
</template>

<style>
body {
  margin: 0;
  padding: 0;
}
#map {
  height: 400px;
  width: 100%;
}
</style>

<script>
/* global mapboxgl */

export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      places: [
        { lat: 41.947460, lng: -87.654730, description: "Home of Elwood Blues" },
        { lat:41.852180, lng: -87.808490, description: "Largest Dead Clown Graveyard in World" }
      ]
    };
  },
  created: function() {},
  mounted: function() {
    mapboxgl.accessToken =
      "pk.eyJ1IjoicGV0ZXJ4amFuZyIsImEiOiJjam94YWZieXExYnQ0M3BucXZwbmV2Y2VsIn0.pmLbX0YPw86c5r8YlyZr7w";
    var map = new mapboxgl.Map({
    //   container: 'map', // container id
    //   style: 'mapbox://styles/mapbox/streets-v9', // stylesheet location
    //   center: [-87.640010, 41.779830], // starting position [lng, lat]
    //   zoom: 9 // starting zoom
    container: "map", // container id
      style: "mapbox://styles/mapbox/streets-v9", // stylesheet location
      center: [this.places[0].lng, this.places[0].lat], // starting position [lng, lat]
      zoom: 3 // starting zoom
    });
     // for (var i = 0; i < this.places.length; i++) {
    //   var place = this.places[i];
    //   var popup = new mapboxgl.Popup({ offset: 25 }).setText(place.description);
    //   var marker = new mapboxgl.Marker()
    //     .setLngLat([place.lng, place.lat])
    //     .setPopup(popup)
    //     .addTo(map);
    // }
    this.places.forEach(function(place) {
      var popup = new mapboxgl.Popup({ offset: 25 }).setText(place.description);
      var marker = new mapboxgl.Marker()
        .setLngLat([place.lng, place.lat])
        .setPopup(popup)
        .addTo(map);
    });
    // var popup = new mapboxgl.Popup({ offset: 25 })
    //   .setText("H.H. Holmes MURDER CASTLE was located at 63rd and Wallace Street. Now a Post Office");
    // var marker = new mapboxgl.Marker()
    // .setLngLat([-87.640010, 41.779830])
    // .setPopup(popup)
    // .addTo(map);
  },
  methods: {},
  computed: {}
};

// Blog app
// var axios = require("axios");

// export default {
//   data: function() {
//     return {
//       message: "VUEJS-BLOG-APP HOME.VUE",
//       posts: []
//     };
//   },
//   created: function() {
//     axios.get("http://localhost:3000/api/posts").then(
//       function(response) {
//         console.log(response.data);
//         this.posts = response.data;
//       }.bind(this)
//     );
//   },
//   methods: {},
//   computed: {}
// };
</script>