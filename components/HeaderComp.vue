
<template>
  <header>
    <div id="Logo">
        <a href="#/" aria-current="page" class="router-link-exact-active router-link-active"><img src="@/assets/voucher_shop.jpg" alt="Vouchershop.nl"/></a>
    </div>
    <div id="HeaderContent">
        <div id="HeaderNav">
            <div id="Links"><a href="#/about" class="">Over Vouchershop</a><a href="#/contact" class="">Contact</a></div>
        </div>
        <div id="HeaderSpace">
            <div id="Cart" class=""><p>€0,00</p></div>
        </div>
    </div>
  </header>
  <div id="PageMenu">
    <div id="PageMenuContent">
      <div id="Categories">
        <div mode="out-in">
            <NuxtLink class="category" to="/">Home</NuxtLink>
            <NuxtLink class="category" to="/category/beltegoed">Beltegoed</NuxtLink>
            <NuxtLink class="category" to="/category/gaming">Gaming</NuxtLink>
            <NuxtLink class="category" to="/category/payment">Payment</NuxtLink>
            <NuxtLink class="category" to="/category/giftcards">Giftcards</NuxtLink>
            <NuxtLink class="category" to="/category/topups">Topups</NuxtLink>
            <NuxtLink class="category" to="/category/coupons">Coupons</NuxtLink>
          <!-- <a href="#/category/topups" class="category btg"><img src="@/assets/btg.svg" />Beltegoed</a><span class="sep">|</span>
          <a href="#/category/giftcards" class="category credit"><img src="@/assets/credit.svg" />Giftcards &amp; Credit</a> -->
        </div>
      </div>
    </div>
  </div>
  <BreadCrumb/>
</template>

<script lang='ts'>
import { state, actions } from '../store/reactives'
import { defineComponent, onMounted, toRaw , ref} from 'vue'

export default defineComponent({
  setup() {
    /// SETUP ROUTING HERE FOR NAVIGATION
    // const router = useRouter()
    const route = useRoute()
    const newPath = ref()

    onMounted(() => {
        route.params._categoryslug ? actions.setCategory(route.params._categoryslug) : console.log('No category');
        route.params._brandslug ? actions.setSelectedBrand(route.params._brandslug) : console.log('No brand');
        route.params._subcat ? actions.setSelectedSubCategory(route.params._subcat) : console.log('No _subcat');
    })

    watch(
      () => route.query,
      async getQuery => {
        console.log('---New Query---', route.params._categoryslug )
        actions.setCategory(route.params._categoryslug)
      }
    )
    return {}
  },
})
</script>



<style lang="scss" scoped>  
  header{
    flex: 0 1 20%;
    min-width: 990px;
    text-align: left;
    margin: 1.2em auto 0.5em;
    display: flex;
    max-height: 80px;

    #Logo{
      flex: 1 1 20%;
      &:active{
          opacity: 0.89;
          transform: translateY(0.6px);
      }
    }
    #HeaderContent{
      flex: 1 1 80%; 
      display: flex;
      flex-flow: column;
    }

    #HeaderNav {
      text-align: right;
      display: flex;
      justify-content: flex-end;

      a {
        font-weight: bold;
        color: #2c3e50;
        display: inline-block;
        // min-width: 100px;
        margin: 0px 20px;
        &:active{
          transform: translateY(1px);
          opacity: 0.9;
        }
        &:last-child {
          margin-right:0;
        }
        &.router-link-exact-active {
          color: #ed6c23;
        }
      }
      #Links{
        a{
          text-decoration: none;
          border-bottom: 2px solid orange
        }
      }
      #Lang{
        flex: 0 1 30%;

        a{
          display: inline;
          margin: 5px;
          width: 50px;
          height: 35px;
          text-align: center;
          cursor: pointer;
        }
      }
    }
    #HeaderSpace {
      padding-top: 1em;
      display: flex;
      justify-content: flex-end;
      #Cart{
        background: #DDD url('./assets/cart.png') no-repeat left;
        background-position: top 4px left 5px;
        background-size: 24px;
        border-radius: 7px;
        text-align: center;
        display: inline-block;
        padding: 5px;
        padding-left: 50px;
        min-width: 55px;
        font-weight: bold;
        color: #626262;
        cursor: pointer;
        border: 2.5px solid #DDD;

        &.filled{
          border: 2.5px solid #ffa502;
          background: #FFF url('./assets/cart_hl.png') no-repeat left;
          background-position: top 4px left 5px;
          background-size: 24px;
        }

        p{
          margin: 0px;
        }

        &:active{
          opacity: 0.89;
          transform: translateY(0.6px);
        }

      }
    }
  }
  #PageMenu{
    // min-height: 60px;
    // max-height: 60px;
    display: block;
    background: repeating-linear-gradient(45deg, #1684c8, #308ac3 100px);
    // overflow: hidden;
    // margin-bottom: 2em;
    
    #PageMenuContent{
      display: flex;
      max-width: 990px;
      margin: 0px auto;
      justify-content: space-between;
      flex: 1 1 100%;
      flex-flow: row wrap;
    }

    #Search{
      padding: 10px;
      input{
        border-radius: 7px;
        border: 1px solid #DDD;
        line-height: 1.2em;
        font-size: 18px;
        box-shadow: inset 1px 1px 1px #00000030;
        outline: none;
        padding: 5px;
        padding-left: 12px;
      }
    }

    #Categories{
      text-align: left;
      display: flex;
      flex: 100%;

      .gaming img {
        -webkit-filter: invert(98%) sepia(99%) saturate(2%) hue-rotate(278deg) brightness(110%) contrast(100%);
        filter: invert(98%) sepia(99%) saturate(2%) hue-rotate(278deg) brightness(110%) contrast(100%);
      }

      & > div{
        display: flex;
        flex: 100%;
      }
      .homebutton {
        line-height:38px;
        vertical-align: middle;
        flex: 1 1 14%;
        img {
          -webkit-filter: invert(98%) sepia(99%) saturate(2%) hue-rotate(278deg) brightness(110%) contrast(100%);
          filter: invert(98%) sepia(99%) saturate(2%) hue-rotate(278deg) brightness(110%) contrast(100%);
          height: 30px;
          margin:2px .5em 0 0em;
          vertical-align: middle;
          transition: .3s ease filter;        
        }
        &:hover img {
          -webkit-filter: invert(53%) sepia(43%) saturate(4403%) hue-rotate(353deg) brightness(98%) contrast(92%);
          filter: invert(53%) sepia(43%) saturate(4403%) hue-rotate(353deg) brightness(98%) contrast(92%);
        }
      }
    }

    .sep{
      align-self: center;
      width: 2px;
      display: inline-block;
      margin-right: .25em;
      margin-left: .25em;
      color: #FFF;
      flex: 0 0 2px;
    }
    .category{
      align-self: center;
      font-size: 17px;
      padding: 5px;
      font-weight: bold;
      text-transform: uppercase;
      display: inline-block;
      text-decoration: none;
      font-weight: bold;
      color: #FFF;
      cursor: pointer;
      //min-width: 175px;
      flex: 0 1 16.6666%;
      transition: .3s ease opacity;
      &:active{
        transform: scale(0.99) translateY(1px);
      }
      &.router-link-exact-active{
        color:orange;
        text-shadow: 0px 0px 3px #00000050;
      }
      img{
        display: inline;
        max-width: 40px;
        max-height: 1.5em;
        float: left;
        margin-right: 0.5em;
      }
      &:hover {
        opacity:.7;
      }
      &.credit{
        // flex: 1 1 33%;
      }    
      &.homebutton{
        flex: 1 1 14%;
      }
      &.gaming {
        flex: 0 1 15%;
      }    
      &.payment {
        flex: 0 1 17%;
      }    
      &.credit {
        flex: 0 1 18%;
      }        
      &.btg {
        flex: 0 1 15%;
      }    
      &.coupons {
        flex: 0 1 20%;
      }
    }

    h1{
      color: #FFF;
      padding-top: 1.5em;
      display: inline-block;
    }
  }
  #PageSubMenu {
    nav {
      background: #DDDDDD50;
    }
    ul {
      list-style:none;
      padding:0;
      width: 100%;
      max-width: 1100px;
      margin:0 auto;
      display:flex;
      background: #b8c5ce repeating-linear-gradient(308deg, #9e9e9e0d, #ffffff40 200px);
      clip-path: polygon(0% 0%, 100% 0%, 98% 50%, 95% 100%, 95% 100%, 100% 100%, 5% 100%, 2% 50%);

      li {
        margin: 0;
        padding: 0;
        line-height: 18px;
        vertical-align: middle;
        -webkit-box-flex: 1;
        align-self: center;
        font-size: 15px;
        padding: 5px;
        font-weight: bold;
        text-transform: uppercase;
        display: inline-block;
        text-decoration: none;
        font-weight: bold;
        color: #444;
        cursor: pointer;
        -webkit-box-flex: 1;
        -ms-flex: 0 1 25%;
        flex: 0 1 25%;
        transition: .3s ease opacity;
        &:hover {
          opacity: .7;
        }
        a {
          text-decoration: none;
          color: #105a8a;
          &:visited{
            color: #0c4971;
          }
          &:active{
          transform: scale(0.99) translateY(1px);
          }
          &.router-link-exact-active{
            color:#fff;
            text-shadow: 0px 0px 3px #000;
          }
          img{
            display: inline;
            max-width: 40px;
            max-height: 1.5em;
            float: left;
            margin-right: 0.5em;
          }
          &:hover {
            opacity:.7;
          }
        }
      }
    }
  }

  #Breadcrumbs{
    background: #DDDDDD50;
    

    #Trail{
      padding: 5px 0px;
      padding: 0px;
      display: block;
      width: 990px;
      margin: 0 auto;
      text-align: left;
      box-sizing: border-box;
      padding-left:2em;
      i{
        color: #929292;
      }

      a{
        display: inline-block;
        padding-right: 10px;
        padding-left: 10px;
        cursor: pointer;
        user-select: none;
        &:hover{
          opacity: 0.8;
        }
        &:active{
          transform: translateY(1px);
        }
      }

    }
  }  
  .menu a {
    display:inline-block;
    margin-right:20px;
  }
</style>