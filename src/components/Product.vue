<template>
  <div class="product">
    <div :class="'product-inner ' + product.color">
      <div class="product-text-wrap">
        <h2 class="bg-text">{{ product.bgtext }}</h2>
      </div>
      <div class="product-image-wrap">
        <img class="image" :src="product.src" />
      </div>
      <div class="product-detail">
        <h2>{{ product.title }}</h2>
        <p class="product-desc">{{ product.desc }}</p>
        <div class="inner-desc">
          <p class="price">$160</p>
          <button type="submit">Add to Cart</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "product",
  props: ["product"]
};
</script>

<style>
.product {
  flex: 1 1 33.333%;
  width: 100%;
  padding: 25px;
}

.product-inner {
  position: relative;
  padding: 25px;
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  perspective: 1000px;
}

.product-inner.black {
  background-image: linear-gradient(to bottom right, #f4f4f7, #2b2c30);
}
.product-inner.desert {
  background-image: linear-gradient(to bottom left, #dcdae8, #f27b54 50%);
}
.product-inner.ice {
  background-image: linear-gradient(to bottom right, #dfdee3, #c5bbb5 70%);
}

.product-text-wrap {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  z-index: 0;
  overflow: hidden;
  perspective: 1000px;
}

.product-text-wrap h2 {
  color: #000;
  font-size: 128px;
  font-weight: 900;
  opacity: 0.2;
  transform-origin: center;
  text-align: center;
}

.product-image-wrap .image {
  width: 100%;
  filter: drop-shadow(0px 0px 12px rgba(0, 0, 0 0.25));
}

.product-image-wrap {
  position: relative;
  z-index: 1;
  transform-origin: center;
  padding: 10px;
}

.product-detail {
  background-color: #fff;
  padding: 25px;
  margin: 0px -25px -25px;
}

.product-detail h2 {
  font-size: 24px;
  font-weight: 700;
  color: #676767;
  margin-bottom: 15px;
}

.product-desc {
  font-size: 14px;
  line-height: 1.5;
  font-weight: 300;
  color: #676767;
  height: 120px;
}

.inner-desc {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 20px;
}

.price {
  font-weight: 600;
}
button {
  cursor: pointer;
  margin-left: auto;
  padding: 8px 24px;
  text-decoration: none;
  color: linear-gradient(to bottom right, #dfdee3, #c5bbb5 70%);
  font-size: 18px;
  border-radius: 20px;
  transition: 0.4s linear;
  color: #f17850;
  border: 2px solid;
}

button:hover {
  color: red;
}
</style>
