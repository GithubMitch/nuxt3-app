<template>
  <Router-View />
</template>

<style lang="scss">
  /* RESET STYLE SHEET */
  #__nuxt {
      font-family: Avenir,Helvetica,Arial,sans-serif;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      color: #2c3e50;
      display: -webkit-box;
      display: -ms-flexbox;
      display: flex;
      -webkit-box-orient: vertical;
      -webkit-box-direction: normal;
      -ms-flex-flow: column;
      flex-flow: column;
      min-height: 100vh;
      -webkit-box-pack: justify;
      -ms-flex-pack: justify;
      justify-content: space-between;
  }
  html {
    background:repeating-linear-gradient(
      -137deg,hsla(0,0%,62%,.050980392156862744),hsla(0,0%,100%,.25098039215686274) 200
      px
      );
  }
  HTML >* , 
  body > * {
    box-sizing: border-box;
    margin:0;
    padding:0;
    font-size:1rem;
    margin-block-start: 0;
    margin-block-end: 0;
    font-family: Avenir,Helvetica,Arial,sans-serif;
  }
  .inner {
    max-width:990px;
    box-sizing:border-box;
    width:100%;
    display:block;
    position:relative;
    margin:auto;
    background: #dedede;
    padding:1em;
    border-bottom:1px solid black;
    &:last-child {
      border:none;
    }
  }
  body {
    padding: 0;
    margin: 0;
    background: repeating-linear-gradient(
    -137deg,hsla(0,0%,62%,.050980392156862744),hsla(0,0%,100%,.25098039215686274) 200px);
    min-height: 100vh;
  }
  .product{
    text-decoration: line-through;
    pointer-events: none;
  }
  .product.instock {
    text-decoration: none;
    pointer-events: all;
  }

  /* Vouchershop component */
  #config-window {
    box-shadow: inset 0px 0px 10px -4px #000; 
    box-sizing:border-box;
    background:#ebebeb;
    height:800px;
    padding:1em;
    overflow: scroll;
    :deep() .brandLine ,
    .brandLine {
      cursor:pointer;
    }
    :deep() .brandLine:hover {
      text-decoration: underline;
    }
  }

  /* product.vue */
  .product-list {
    display: flex;
    align-content: center;
    flex-wrap: nowrap;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
    list-style:none;
    padding:0;
    li {
      width: 32%;
      box-sizing: border-box;
      border: 1px dashed black;
      text-align: center;
      padding: 1em;
      background: #fbfbfb;
      margin: 0.5em 0;
      transition:.3s ease all;
      a {
        transition:.3s ease all;
      }
    }
    li:hover {
      // background:#dedede;
      border:1px solid black;
      a {
        text-decoration: none;
        font-weight:500;
      }
    }  
  }
    /* product.vue */
  .brand-list {
    display: flex;
    list-style: none;
    padding: 0;
    flex-direction: row;
    flex-wrap: wrap;
    list-style: none;
    padding: 0;
    justify-content: space-between;
    li {
      width: 32%;
      box-sizing: border-box;
      border: 1px dashed black;
      text-align: center;
      padding: 1em;
      background: #fbfbfb;
      margin: 0.5em 0;
      transition:.3s ease all;
      a {
        transition:.3s ease all;
      }
    }
    li:hover {
      // background:#dedede;
      border:1px solid black;
      a {
        text-decoration: none;
        font-weight:500;
      }
    }  
  }
</style>