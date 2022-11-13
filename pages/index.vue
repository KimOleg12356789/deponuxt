<template>
    <div>
      <div class="modal js-modal" data-modal="1">
        <div class="modal__inner modal-border">
          <div class="modal-title">
            Заголовок попапа
          </div>
          <div class="modal-suptitle">
            Широкий спектр услуг по торговле и управлению цифровыми активами для удовлетворения разнообразных торговых потребностей. 
          </div>

          <button class="modal-close">
            <img class="button-close-modal js-close-modal" src="assets/images/modal-close.svg" alt="">
          </button>
          
          <div class="modal-button">
            <button class="button-close-modal js-close-modal">Button</button>
          </div>
        </div>
      </div>


      <div class="modal js-modal" data-modal="2">
        <div class="modal__inner modal-border">
          <div class="modal-close">
            <button >
              <img class="button-close-modal js-close-modal" src="assets/images/modal-close.svg" alt="">
            </button>
          </div>
          <div class="modal-title">
            Заголовок попапа
          </div>
          <div class="modal-form">
            <div class="modal-input-title">
              Выберите страну
            </div>
            <div class="modal-input">
              <div class="modal-input-button">
                <button>
                  <img src="assets/images/modal-input-button.svg" alt="">
                </button>
              </div>
              <input type="text" size="40" placeholder="Выберите страну">
            </div>
            <div class="modal-input-title">
              Имя
            </div>
            <div class="modal-input">
              
              <input type="text" size="40" placeholder="Напишите свое имя ">
            </div>
            <div class="modal-input-title">
              Email
            </div>
            <div class="modal-input">
              
              <input type="text" size="40" placeholder="Напишите свой email">
            </div>
          </div>
          <div class="modal-button3">
            <button>Отправить заявку</button>
          </div>
        </div>
      </div>
        
    </div>
</template>

<!-- <script>
export default {
  name: 'IndexPage'
}

</script> -->




<script>
  export default {
    mounted() {

      let triggersModal = document.querySelectorAll(".js-show-modal");
      let modals = document.querySelectorAll(".js-modal");

      function closeModal() {
        modals.forEach(modal => {
          if (modal.classList.contains("is-open")) {
            modal.classList.remove("is-open");
          }
        });
      }

      triggersModal.forEach((button) =>
      button.addEventListener("click", function (e) {
        e.preventDefault();
        let modalID = this.dataset.modal;
        console.log(modalID);
        modals.forEach(function (modal) {
          if (modal.dataset.modal == modalID) {
            modal.classList.add("is-open");
          }
        });
      }));


      modals.forEach(modal => {
        modal.addEventListener("click", function (event) {
          const isOutside = !event.target.closest(".modal__inner");
          const isCloseButton = event.target.matches(".js-close-modal");
          if (isCloseButton || isOutside) {
            closeModal();
          }
        });
      });

      window.addEventListener("keydown", event => {
        if (event.key === "Escape") {
          closeModal();
        }
      });

      const burger = document.querySelector('.burger');
      const navbar = document.querySelector('.mt-mobile');
      const body = document.querySelector('body');

      burger.addEventListener('click', () => {
          navbar.classList.toggle('nav-open');
          body.classList.toggle('body-open');
          burger.classList.toggle('burger-open');
          
      });


      const items = document.querySelectorAll(".item");

      items.forEach((item) => {
          item.addEventListener("click", () => {
              item.classList.toggle("open");
          });
      });

      const anchors = document.querySelectorAll('a[href*="#"]')

      for (let anchor of anchors) {
        anchor.addEventListener('click', function (e) {
          e.preventDefault()
          
          const blockID = anchor.getAttribute('href').substr(1)
          
          document.getElementById(blockID).scrollIntoView({
            behavior: 'smooth',
            block: 'start'
          })
        })
      };
    },
  };
</script>