<!-- TOP -->
<div class="top">
  <img class="scenario-academy-logo" src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-2023.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Shopping Cart Data Modeling</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span>
  </div>
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step1-astra"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 2 of 10</span>
 <a href='command:katapod.loadPage?[{"step":"step3-astra"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Create tables</div>


✅ Create table `carts_by_user`:
```
CREATE TABLE IF NOT EXISTS carts_by_user (
  user_id TEXT,
  cart_name TEXT,
  cart_id UUID,
  cart_is_active BOOLEAN,
  user_email TEXT STATIC,
  PRIMARY KEY ((user_id),cart_name,cart_id)
);
```

✅ Create table `items_by_id`:
```
CREATE TABLE IF NOT EXISTS items_by_id (
  id TEXT,
  name TEXT,
  description TEXT,
  price DECIMAL,
  PRIMARY KEY ((id))
);
```

✅ Create table `items_by_name`:
```
CREATE TABLE IF NOT EXISTS items_by_name (
  name TEXT,
  id TEXT,  
  description TEXT,
  price DECIMAL,
  PRIMARY KEY ((name), id)
);
```

✅ Create table `items_by_cart`:
```
CREATE TABLE IF NOT EXISTS items_by_cart (
  cart_id UUID,
  timestamp TIMESTAMP,
  item_id TEXT,
  item_name TEXT,
  item_description TEXT,
  item_price DECIMAL,
  quantity INT,
  cart_subtotal DECIMAL STATIC,
  PRIMARY KEY ((cart_id),timestamp,item_id)
) WITH CLUSTERING ORDER BY (timestamp DESC, item_id ASC);
```

✅ Verify that the four tables have been created:
```
DESCRIBE TABLES;
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step1-astra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step3-astra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
