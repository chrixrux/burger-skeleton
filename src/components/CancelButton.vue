<template>
  <div class="cancelButton">

<!--warning message -->
  <transition name="modal">
    <div class="modal">
      <div v-if="isOpen">
        <div class="overlay" @click.self="isOpen = false">
          <div class="modal">
           
           <header class="modal-header">
              <slot name="header">
                <p class = "text"> {{uiLabels.cancelWarning}} </p>
                  <button
                    type="button"
                    class="btn-close"
                    @click = "isOpen = false">
                        <span class = "text"> x </span>
                  </button>
              </slot>
            </header>
           
           <section class="modal-body">
              <slot name="body">
                <p class = "text">
                    {{uiLabels.cancelText}}
                </p>
              </slot>
            </section>
            
            <footer class="modal-footer">
              <slot name="footer">
                <router-link id="routerLink" to="/">
                <button
                    type="button"
                    class="btn-choice"
                    id="btn-yes"
                    @click="isOpen = false"
                    
                    >
                    {{uiLabels.yes}}
                </button>
                </router-link>
                <button
                  type="button"
                  class="btn-choice"
                  id="btn-no"
                  @click="isOpen = false">
                      {{uiLabels.no}}
                </button>
               </slot>
             </footer>
          </div>
        </div>
      </div>
    </div>
 </transition>

<!--button -->
    <label>
      <button id="cancelButton"
      @click="isOpen = !isOpen">
       <p id="cancelButtonText">{{uiLabels.cancelButtonText}}</p>
     </button>
    </label>
  </div>
</template>

<script>
export default {
  name: 'CancelButton',
  props: {
  uiLabels: Object,
  lang: String
  },
  data: function() {
    return {
      isOpen: false
    };
  }
}
</script>

<style scoped>
  #cancelButton {
    background-color: #F08080;
    border-radius: 10px;
    border: 2px solid grey;
    padding-left: 20px;
    padding-right: 20px;
    width: 200px;
    height: 40px;
    align-self: center;
    text-align: center;
    margin-right: 20px;
    outline: none;
}
#cancelButton:hover, cancelButton:active {
    cursor: pointer;
    box-shadow: 0 12px 16px 0 rgba(0,0,0,0.24), 0 17px 50px 0 rgba(0,0,0,0.19);
    background-color: #ea4848;
}
#cancelButtonText {
    font-family: 'Comfortaa', cursive;
    font-size: 14pt;
    color: darkslategrey;
    position: relative;
    left: 50%;
    transform: translate(-50%, -50%);
}
#routerLink {
  margin: auto;
}
.modal {
    background: #e7e7e7;
    overflow-x: auto;
    display: flex;
    flex-direction: column;
    text-align: center;
}
.modal-header,
.modal-footer {
    padding: 15px;
    display: flex;
}

.modal-header {
    padding-left: 30px;
    border-bottom: 1px solid #eeeeee;
    font-size: 32px;
}
.modal-footer {
    border-top: 1px solid #eeeeee;
 }
 .modal-body {
    position: relative;
    padding: 20px 10px;
 }

.text {
    font-family: 'Comfortaa', cursive;
    color: darkslategrey;
}
.bold {
    font-weight: bold;
}

.fadeIn-enter {
  opacity: 0;
}
.fadeIn-leave-active {
  opacity: 0;
  transition: all 0.2s step-end;
}
.fadeIn-enter .modal,
.fadeIn-leave-active.modal {
  transform: scale(1.1);
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background: #00000094;
  z-index: 999;
  transition: opacity 0.2s ease;
}

.btn-close {
    margin-left: 20px;
    border: none;
    width: 20px;
    height: 20px;
    font-size: 16px;
    cursor: pointer;
    font-weight: bold;
    background: transparent;
    text-align: center;
}
.btn-choice {
    padding: 7px;
    margin: auto;
    color: white;
    border: 1px solid #4AAE9B;
    border-radius: 2px;
    font-size: 1.1rem;
    cursor: pointer;
    width: 100px;
    outline: none;
}
#btn-yes {
    background: #8FBC8F;
}
#btn-yes:hover, btn-no:active {
  background:  #609f60;
}
#btn-no {
    background: #F08080;
}
#btn-yes:hover, btn-no:active {
  background:  #609f60;
}
</style>
