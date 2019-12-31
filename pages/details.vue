<template>
  <div id="rootNode">
    <div> je gere pas laffichage des reponse au reponse d'un commentaire (javais pas envie de reflechir) </div>
    <h1 style="text-align:center"> {{product.product_name}}</h1>
    <div class="product_img">
      <img class="product_img_main" id="current_img" :src="selected_img==''?product.img[0]:selected_img">
      <div class="product_img_items">
        <img class="img_items" v-for=" (img,index) in product.img " @click="selected_img=product.img[index]" :key="index" :src="img">
      </div>

      <ul>
        <li v-for="component in product.composition" :key="component.name">
          {{`${component.name} : ${component.pourcentage}%`}}
        </li>
      </ul>

      <div class="comment_container">
        <div class="comment" v-for="comment in comments" :key="comment._id">
          <div class="comment_header">
            <h3 class="comment_header_title">{{comment.title}}</h3>
            <span class="comment_header_user">{{comment.userId}}</span>
          </div>
          <div class="comment_content">
            {{comment.content}}
          </div>
          <div class="response" v-for="resp in response.filter((item)=>item.comment_id==comment._id)" :key="resp._id">
            <div class="comment_header">
              <h3 class="comment_header_title">{{resp.title}}</h3>
              <span class="comment_header_user">{{`${resp.userId} to ${comment.userId}`}}</span>
            </div>
            <div  class="comment_content" >
            {{resp.content}}
          </div>
          </div>
        </div>
        </div>
      </div>


    <div>
      {{ 'votre id produit obtenus apres le nuxt link (ceci est afficher si la page est pas refresh) '+product_id}}
    </div>
  </div>

</template>

<script>
  export default {
    data() {
      return {
        product_id: '',
        product: {
          _id: 'gecgtf',
          product_name: 'ice tea',
          brand: 'coca cola company',
          note: 2,
          img: ['https://www.poulaillon.fr/boutique/724-large_default/lipton-ice-tea-50-cl.jpg',
            'https://boulangerie-paul.lu/media/small/66-bouteille-ice-tea-peche-lipton.jpeg'],
          composition: [
            {
              name: 'thé',
              pourcentage: 10
            },
            {
              name: 'extrait de peche',
              pourcentage: 10
            },
            {
              name: 'sugar',
              pourcentage: 20
            },
            {name: 'eau', pourcentage: 60}
          ]
        },

        comments: [
          {
            _id: '0',
            content: ' une boisson rafraichissante malgres son taux de sucre  élevé',
            userId: 'phillipe_le_gastronome',
            title: `c'eest sucré mais bon`
          },
          {
            _id: '1',
            content: ' si tu regarde ce commentaire cest qu je suis arriver au bout des commentaire',
            userId: 'dorian',
            title: `désoler si jai rendu tard `
          },
        ],
        response: [
          {_id: 'efdead65', comment_id:'0', content: 'cest une boisson commune que  parent et enfant adore', userId: 'le_cuistot_du_coin', title: `un classique des petit restos`},
          {_id: 'qsfljqd4', comment_id: '0', content: ' cette boisson est une insulte a la gastronomie , il devrait etre retiré des supermarché  et tu devrais rendre ton tablier @le_cuistot_du_coin ', userId: 'gordon_ramsay', title: `la honte des boisson`}],
        selected_img:'',
      };
    },

    mounted() {
      this.product_id = this.$route.params.id;
      //pensez a mettre en localstorage  pour que le f5 ne fasse pas perdre le n° du produit
    }
  };
</script>

<style scoped>
div{
  text-align: center;
}
#rootNode{
  display: flex;
  flex-direction:column;
  align-items: center;
}
  .product_img {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .product_img_items {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }

  .product_img_main {
    width: 200px;
    height: 250px;
    border: solid black 1px;
    padding: 2px;
  }

  .img_items {
    width: 75px;
    height: 100px;
    border: solid black 1px;
    padding: 2px;
  }

  .comment_container{
    width: 70%;
  }
  .comment{
    margin: 20px 0px;
    padding: 14px;
  }
  .comment_header_title{
    font-size: 1.1em;
    color: #00bd00;
  }
  .comment_header_user{
    color: #CA8200;
    opacity: 80%;
    font-size: 0.6em;
    text-align:left;
  }
  .comment_content{
    background-color: #f0f1ff;
    text-align:left;
    font-size: 0.9em;
  }
  .response{
    border-bottom: black 1px solid;
    margin-bottom: 10px;
  }
</style>
