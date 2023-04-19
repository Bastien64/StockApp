<template>
    <main>
        <div class="StockBox">
            <h1>Le <span class="letter">S</span>tock <span class="letter">E</span>x <span class="letter">A</span>pp</h1>
            <p>Voici les trois valeurs à suivre en crypto:</p>
        </div>
     <NotificationCrypto/>
    </main>
  </template>
  <style scoped>
  .StockBox {
      max-width: 40%;
      margin-top: 10%;
      margin-left: 10%;
      box-shadow: 4px 4px 1px 4px #00000025;
      border-radius: 10px;
      padding: 5px;
  }
  h1 {
      font-weight: bolder;
  }
  
  .letter {
      color: blueviolet;
  }</style>