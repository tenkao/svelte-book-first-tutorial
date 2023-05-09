<script>
  // カートに入っている商品IDの配列
  let cart = []

  // カートに商品を追加する関数
  function addToCart(productId) {
    cart = [...cart, productId]
  }
</script>

<header class="header">
  <a href="/" class="header-title">Svelte EC</a>
  <nav>
    <ul class="header-link">
      <li>ようこそゲストさん</li>
      <li>
        <a href="/cart">カート (0)</a>
      </li>
    </ul>
  </nav>
</header>

<article class="product">
  <div class="product-main">
    <div class="image-container">
      <img src="https://github.com/svelte-book/sample-app/raw/main/static/svelte-book-1.png" alt="『Svelte Guide』表紙">
    </div>
    <div>
      <h2>Svelte Guide</h2>
      <dl>
        <dt>価格</dt>
        <dd>3,500円</dd>
      </dl>
      <div>
        {#if !cart.includes('svelte-book')}
          <button on:click={() => addToCart('svelte-book')}>カートに入れる</button>
        {:else}
          <button disabled>カート追加済み</button>
        {/if}
      </div>
    </div>
  </div>
  <footer>
    <h3>関連商品</h3>
    <ul>
      <li><a href="/products/react-book">React Book</a> - 3,500円</li>
      <li><a href="/products/vue-book">Vue Book</a> - 3,500円</li>
      <li><a href="/products/angular-book">Angular Book</a> - 3,500円</li>
    </ul>
  </footer>
</article>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    background-color: #eee;
  }

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0 auto;
    background-color: #fff;
    padding: 0 15px;
    width: 100%;
    max-width: 800px;
    height: 50px;
  }

  .header-title {
    font-weight: bold;
  }
  
  .header-link {
    display: flex;
    gap: 10px;
    margin: 0;
    padding: 0;
    list-style: none;
  }

  .product {
    margin: 0 auto;
    background-color: #fff;
    padding: 15px;
    width: 100%;
    max-width: 800px;
  }

  .product-main {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
  }

  .image-container {
    width: 100%;
    max-width: 400px;
    overflow: hidden;
  }

  .image-container img {
    width: 100%;
  }
</style>
