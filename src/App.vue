<template>
  <main id="app" @mousemove="mousemove">
    <div class="logo">
      <img src="./assets/orange.png" alt="Nike" />
    </div>
    <div class="container">
      <section class="products">
        <Product
          v-for="product in products"
          :key="product.color"
          :product="product"
        />
      </section>
    </div>
  </main>
</template>

<script>
import Product from "./components/Product";
// import { gsap } from "gsap";

export default {
  name: "App",
  components: {
    Product
  },
  data() {
    return {
      products: [
        {
          title: "OFF-WHITE x Air Max 90 'Black'",
          color: "black",
          bgtext: "NIKE",
          desc:
            "This AM 90 is sporting a black upper, white Nike “Swoosh”, black midsole, and a black sole. These sneakers released in January 2019 and retailed for $160.",
          src: require("./assets/am-blk.png")
        },
        {
          title: "OFF-WHITE x Air Max 90 'Desert Ore'",
          color: "desert",
          bgtext: "AIR",
          desc:
            "This AM 90 comes with a beige upper, mango orange Nike “Swoosh”, beige midsole, and beige sole. These sneakers released in January 2019 and retailed for $160.",
          src: require("./assets/am-ds.png")
        },
        {
          title: "OFF-WHITE x Air Max 90 'The Ten'",
          color: "ice",
          bgtext: "MAX",
          desc:
            "This AM 90 combines a white leather upper with ice blue foam and grey suede overlays, a stitched reflective white Nike Swoosh, signature orange tag, and a grey suede heel patch. These sneakers released in January 2019 and retailed for $160.",
          src: require("./assets/am-wht.png")
        }
      ]
    };
  },
  methods: {
    mousemove(e) {
      let mouseX = e.clientX;
      let mouseY = e.clientY;

      let products = document.querySelectorAll(".products, .product");
      for (let i = 0; i < products.length; i++) {
        let product = products[i];

        let product_image = product.querySelector(".product-image-wrap");

        let img_x = mouseX - this.coords(product_image).x;
        let img_y = mouseY - this.coords(product_image).y;
        product_image.style.transform = `translateY(-${img_y /
          100}px) translateX(-${img_x / 100}px) translateZ(100px)`;

        let bgtext = product.querySelector(".bg-text");
        let bg_x = mouseX - this.coords(bgtext).x;
        // let bg_y = mouseY - this.coords(bgtext).y;
        bgtext.style.transform = `translateX(${bg_x / 70}px)`;
      }
    },
    coords(el) {
      let coords = el.getBoundingClientRect();

      return {
        x: coords.left / 2,
        y: coords.top / 2
      };
    }
  }
};
</script>

<style>
.overlay {
  z-index: 1;
  position: absolute;
  width: 100%;
  height: 100vh;
  background: #fff;
  top: 0;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "montserrat", sans-serif;
}

.container {
  width: 100vw;
  min-height: 100vh;
  overflow: hidden;
  background-color: #eee;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color: #eee;
}

.products {
  display: flex;
  max-width: 1280px;
  padding: 25px;
  flex-direction: row;
}

.logo {
  height: 100px;
  display: flex;
  background-color: #eee;
}

.logo img {
  max-width: 100%;
  max-height: 100%;
}

@media (max-width: 900px) {
  .products {
    flex-direction: column;
  }

  .product-image-wrap img {
    height: auto;
    width: 50%;
  }

  .bg-text {
    font-size: 13rem !important;
  }

  .product-detail {
    font-size: 1rem;
  }
}
</style>
