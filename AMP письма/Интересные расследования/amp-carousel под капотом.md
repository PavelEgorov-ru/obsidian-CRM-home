
Мы формируем следующий блок

```
.product-ribbon {
      display: flex;
      background: #f0f0f0;
    }
.product-card {
      flex: 0 0 160px;
      margin: 10px;
      background: white;
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      display: flex;
      flex-direction: column;
    }
    
.product-card .card-text {
      padding: 8px;
      font-size: 14px;
      flex-grow: 1;
    }
    
.product-card .card-text .price {
      font-weight: bold;
      color: #d32f2f;
      margin-top: 4px;
    }

<amp-carousel class="product-ribbon" type="carousel" layout="fixed-height" height="250" width="auto">

      <!-- Карточка 1 -->
      <div class="product-card">
        <amp-img src="https://rassylka.static1-sima-land.com/ftp_rassylka/000032743-1/0000.png" layout="responsive" width="160" height="120" alt="Товар 1">
        </amp-img>
        <div class="card-text">
          <div>Яркая футболка</div>
          <div class="price">1500 ₽</div>
        </div>
      </div>  

      <!-- Карточка 2 -->
      <div class="product-card">
        <amp-img src="https://rassylka.static1-sima-land.com/ftp_rassylka/000032743-1/0000.png" layout="responsive" width="160" height="120" alt="Товар 2">
        </amp-img>
        <div class="card-text">
          <div>Удобные джинсы</div>
          <div class="price">3200 ₽</div>
        </div>
      </div>  

      <!-- Карточка 3 -->
      <div class="product-card">
        <amp-img src="https://rassylka.static1-sima-land.com/ftp_rassylka/000032743-1/0000.png" layout="responsive" width="160" height="120" alt="Товар 3">
        </amp-img>
        <div class="card-text">
          <div>Стильные кроссовки</div>
          <div class="price">4900 ₽</div>
        </div>
      </div>
      
</amp-carousel>
```


что в реальности формируется в браузере

```
<amp-carousel class="product-ribbon i-amphtml-element i-amphtml-layout-fixed-height i-amphtml-layout-size-defined i-amphtml-carousel-has-controls i-amphtml-built i-amphtml-layout" type="carousel" layout="fixed-height" height="250" width="auto" i-amphtml-layout="fixed-height" style="height: 250px;" i-amphtml-carousel-hide-buttons="">
    <div class="i-amphtml-scrollable-carousel-container" tabindex="-1"><div class="product-card amp-carousel-slide amp-scrollable-carousel-slide">
        <amp-img src="https://rassylka.static1-sima-land.com/ftp_rassylka/000032743-1/0000.png" layout="responsive" width="160" height="120" alt="Товар 1" class="i-amphtml-element i-amphtml-layout-responsive i-amphtml-layout-size-defined i-amphtml-built i-amphtml-layout" i-amphtml-layout="responsive" style="--loader-delay-offset: 13ms !important;"><i-amphtml-sizer slot="i-amphtml-svc" style="padding-top: 75%;"></i-amphtml-sizer>
        <img decoding="async" alt="Товар 1" src="https://rassylka.static1-sima-land.com/ftp_rassylka/000032743-1/0000.png" class="i-amphtml-fill-content i-amphtml-replaced-content"></amp-img>
        <div class="card-text">
          <div>Яркая футболка</div>
          <div class="price">1500 ₽</div>
        </div>
      </div><div class="product-card amp-carousel-slide amp-scrollable-carousel-slide">
        <amp-img src="https://rassylka.static1-sima-land.com/ftp_rassylka/000032743-1/0000.png" layout="responsive" width="160" height="120" alt="Товар 2" class="i-amphtml-element i-amphtml-layout-responsive i-amphtml-layout-size-defined i-amphtml-built i-amphtml-layout" i-amphtml-layout="responsive" style="--loader-delay-offset: 12ms !important;"><i-amphtml-sizer slot="i-amphtml-svc" style="padding-top: 75%;"></i-amphtml-sizer>
        <img decoding="async" alt="Товар 2" src="https://rassylka.static1-sima-land.com/ftp_rassylka/000032743-1/0000.png" class="i-amphtml-fill-content i-amphtml-replaced-content"></amp-img>
        <div class="card-text">
          <div>Удобные джинсы</div>
          <div class="price">3200 ₽</div>
        </div>
      </div><div class="product-card amp-carousel-slide amp-scrollable-carousel-slide">
        <amp-img src="https://rassylka.static1-sima-land.com/ftp_rassylka/000032743-1/0000.png" layout="responsive" width="160" height="120" alt="Товар 3" class="i-amphtml-element i-amphtml-layout-responsive i-amphtml-layout-size-defined i-amphtml-built i-amphtml-layout" i-amphtml-layout="responsive" style="--loader-delay-offset: 13ms !important;"><i-amphtml-sizer slot="i-amphtml-svc" style="padding-top: 75%;"></i-amphtml-sizer>
        <img decoding="async" alt="Товар 3" src="https://rassylka.static1-sima-land.com/ftp_rassylka/000032743-1/0000.png" class="i-amphtml-fill-content i-amphtml-replaced-content"></amp-img>
        <div class="card-text">
          <div>Стильные кроссовки</div>
          <div class="price">4900 ₽</div>
        </div>
      </div></div><div tabindex="-1" class="amp-carousel-button amp-carousel-button-prev amp-disabled" role="presentation" title="Previous item in carousel" aria-disabled="true"></div><div tabindex="-1" class="amp-carousel-button amp-carousel-button-next amp-disabled" role="presentation" title="Next item in carousel" aria-disabled="true"></div></amp-carousel>
```