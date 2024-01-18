<!-- ShoeSearch.svelte -->

<script lang="ts">
    interface ShoeDatabase {
      brand: string;
      size: number;
      stackHeight: number;
      durability: string;
      color: string;
      price: number;
    }
  
    let brand: string = "";
    let size: number = 0;
    let stackHeight: number = 0;
    let durability: string = "";
    let color: string = "";
    let price: number = 0;
  
    let shoeDatabase: ShoeDatabase[] = [
      { brand: "Nike", size: 10, stackHeight: 30, durability: "High", color: "Red", price: 100 },
      { brand: "Adidas", size: 9, stackHeight: 25, durability: "Medium", color: "Blue", price: 80 },
      // Add more shoe entries as needed
    ];
  
    let searchResults: ShoeDatabase[] = [];
  
    function searchShoes() {
      searchResults = shoeDatabase.filter(shoe => 
        shoe.brand.toLowerCase().includes(brand.toLowerCase()) &&
        (shoe.size >= size || size == 0 || size == null) &&
        (shoe.stackHeight >= stackHeight || stackHeight == 0 || stackHeight == null) &&
        (shoe.durability.toLowerCase().includes(durability.toLowerCase()) || durability == ""  || durability == null) &&
        (shoe.color.toLowerCase().includes(color.toLowerCase()) || color == "" || color == null) &&
        (shoe.price <= price || price == 0  || price == null)
      );
    }
  </script>
  
  <main>
    <h1>Shoe Search</h1>
  
    <div class="input-column">
      <label for="brand">Brand:</label>
      <input type="text" bind:value={brand} />
    </div>
  
    <div class="input-column">
      <label for="size">Size:</label>
      <input type="number" bind:value={size} />
    </div>
  
    <div class="input-column">
      <label for="stackHeight">Stack Height:</label>
      <input type="number" bind:value={stackHeight} />
    </div>
  
    <div class="input-column">
      <label for="durability">Durability:</label>
      <input type="text" bind:value={durability} />
    </div>
  
    <div class="input-column">
      <label for="color">Color:</label>
      <input type="text" bind:value={color} />
    </div>
  
    <div class="input-column">
      <label for="price">Price:</label>
      <input type="number" bind:value={price} />
    </div>
  
    <button on:click={searchShoes}>Search</button>
  
    {#if searchResults.length > 0}
      <table>
        <thead>
          <tr>
            <th>Brand</th>
            <th>Size</th>
            <th>Stack Height</th>
            <th>Durability</th>
            <th>Color</th>
            <th>Price</th>
          </tr>
        </thead>
        <tbody>
          {#each searchResults as shoe (shoe.brand)}
            <tr>
              <td>{shoe.brand}</td>
              <td>{shoe.size}</td>
              <td>{shoe.stackHeight}</td>
              <td>{shoe.durability}</td>
              <td>{shoe.color}</td>
              <td>{shoe.price}</td>
            </tr>
          {/each}
        </tbody>
      </table>
    {:else}
      <p>No results found.</p>
    {/if}
  </main>
  
  <style>
    main {
      text-align: center;
      margin: 2rem;
    }
  
    .input-column {
      display: inline-block;
      margin: 0 1rem;
    }
  
    label {
      display: block;
      margin-top: 0.5rem;
    }
  
    input {
      margin-bottom: 0.5rem;
    }
  
    button {
      margin-top: 1rem;
    }
  
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 1rem;
    }
  
    th, td {
      border: 1px solid #ddd;
      padding: 8px;
    }
  
    th {
      background-color: #791414;
    }
  </style>
  