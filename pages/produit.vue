<template>
  <div class="main">
    <form action="./">
      <input>
    </form>


    <div class="product" v-for="product in products">
      <img class="product_img" :src="product.img[0]">
      <div class="product_info">

        <!-- a changer pour un state avec son dispatch  lorsque le store seras en place ps elle est inexistante a lheur actuelle -->
        <nuxt-link class="product_name" :to="{name: 'details', params: { id:product._id } }">
          {{product.product_name}}
        </nuxt-link>

        <div class="product_brand">{{product.brand}}</div>
        <div v-if="product.note<=2" class="product_note">
          {{product.note+'/5 Mauvais'}}
        </div>
        <div v-else-if="product.note<=4" class="product_note">
          {{product.note+'/5 Déconseillé'}}
        </div>
        <div v-else class="product_note">
          {{product.note+'/5 Bon'}}
        </div>
      </div>
    </div>
    <div style="display: none">Icons made by <a href="https://www.flaticon.com/authors/smashicons" title="Smashicons">Smashicons</a>
      from <a
        href="https://www.flaticon.co/" title="Flaticon">www.flaticon.com</a></div>
  </div>

</template>

<script>
  export default {
    name: "produit",

    data() {
      return {
        products: [
          {
            _id: 'ereerez',
            product_name: 'caco-calo',
            brand: 'coca cola company',
            note: 0,
            img: ['http://www.urgence-traiteur.com/media/catalog/product/cache/2/small_image/767x/9df78eab33525d08d6e5fb8d27136e95/u/t/utbococa.jpg'],
            composition: [
              {
                name: 'coca',
                pourcentage: 10
              },
              {
                name: 'sugar',
                pourcentage: 50
              },
              {
                name: 'eau',
                pourcentage: 40
              }
            ]
          },
          {
            _id: 'gecgtf',
            product_name: 'ice tea',
            brand: 'coca cola company',
            note: 2,
            img: ['https://www.poulaillon.fr/boutique/724-large_default/lipton-ice-tea-50-cl.jpg'],
            composition: [
              {
                name: 'the',
                pourcentage: 10
              },
              {
                name: 'extrait de peche',
                pourcentage: 10
              },
              {
                name: 'sugar',
                pourcentage: 50
              },
              {name: 'eau'}
            ]
          },
          {
            _id: 'hdtrgs',
            product_name: 'cristaline eau de source',
            brand: 'cristaline',
            note: 5,
            img: [],
            composition: [
              {
                name: 'eau',
                pourcentage: 98
              },
              {
                name: 'sugar',
                pourcentage: 0
              },
              {
                name: 'additif',
                pourcentage: 2
              }
            ]
          },
        ]

      }
    },

  }
</script>
<style scoped>
  .main {
    background-color: #3b8070;
  }

  .product {
    width: 100%;
    height: 90px;
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: row;
    background-color: #d5d6e2;

  }

  .product_info {
    width: 75%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: start;
    padding-left: 20px;
  }

  .product_brand {
    color: grey;
  }

  .product_note {
    align-self: flex-end;
    justify-self: flex-end;
  }

  .product_img {
    width: 97px;
    height: 91px;
    align-self: center;
  }

  .product_name {
    font-size: 1.2em;
    font-weight: bold;
    color: #65c963;
    text-decoration:none;
  }
  .product_name:hover{

    font-size: 1.4em;
    cursor: pointer;
  }

  @media screen and (min-width: 768px) {

    .product_info {
      width: 80%;

    }

    .product_brand {

    }

    .product_img {
      width: 15%;
    }

    .product_name {
      font-size: 1.5em;
    }
  }

</style>
