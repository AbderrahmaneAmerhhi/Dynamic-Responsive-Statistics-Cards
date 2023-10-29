<template>

    <!-- <div class="container-fluid px-4">

         <div class="row g-3 my-2">
             <div class="cadr col-md-3" v-for="(data,index) in data" :key="index">
                <div class=" p-3 bg-white shadow-sm d-flex justify-content-around align-items-center rounded">
                    <div>
                        <h3 class="fs-2">{{data.title}}</h3>
                        <p class="counter fs-5" v-bind:data-target="data.number" >{{data.number}}</p>
                    </div>
                    <i class="fs-1  border  p3 card-icon "></i>
                </div>
             </div>

         </div>
    </div> -->


    <div class=" px-2">

             <div class="row my-2 cards-container">
                 <div class="cadr cadr-element" v-for="(data, index) in data" :key="index" :class="data.cardclass">
                    <div class="card-data" >
                        <div>
                            <h3 class="counter fs-5" v-bind:data-target="data.number" >{{ data.number }}</h3>
                            <h5 class="card-title">{{ data.title }}</h5>
                        </div>
                        <i :id="data.iconId" class="fs-1  border  p3 card-icon "></i>
                    </div>
                 </div>

             </div>
        </div>
</template>

<script>

import '../style/main.css'
export default {
    
  data () {
    return {
    }
  },
  created () {

  },
  mounted() {
      console.log(this.data)
      this.addIcons();
      this.CounterAnimation();
  },
  props: ['data'],
    name:'cards',
    methods: {
        addIcons() {
            if (this.data) {
                for (var i = 0; i < this.data.length; i++) {
                    document.querySelectorAll('.card-icon').forEach((ele, index) => {
                        if (i === index) {
                            ele.classList.remove('bx')
                            ele.classList.remove('bx-stats')
                            if (ele.classList.length > 4) {
                                for (var n = 0; n < ele.classList.length; n++) {
                                    ele.classList.remove('' + ele.classList[n + 4] + '')
                                }
                            }
                            if (this.data[i].icon) {
                                this.data[i].icon.split(' ').forEach(l => ele.classList.toggle(l))

                            } else {
                                var defaultClass = 'bx bx-stats';
                                defaultClass.split(' ').forEach(l => ele.classList.toggle(l))
                            }

                        }

                    });
                }
            }

        },
        CounterAnimation() {
            const counters = document.querySelectorAll('.counter');
            counters.forEach((counter) => {
                counter.innerText = '0';
                const UpdateCounter = () => {
                    const target = +counter.getAttribute('data-target');
                    const c = +counter.innerText;

                    const increment = target / 200;
                    if (c < target) {

                        counter.innerText = `${Math.ceil(c + increment)}`;
                        setTimeout(UpdateCounter, 1)
                    }
                };
                UpdateCounter();
            })


        }

    },
}
</script>


<style>
/* 
.cadr{
   position: relative;

}
.cadr::before{
    content: '';
    width: 6px;
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
    background-color: #232D65;
}

.card-icon{

    width: 60px;
    height: 60px;
    display: grid;
    text-align: center;
    align-items: center;
    background-color: #929DD9;
    color:  #232D65;
    border-radius: 50%;
}
.cadr:hover::before{
    background-color: #929DD9;
}
.cadr:hover .card-icon{
     background-color: #A8B0E0;
}

@media(max-width: 786px){
    .cards-container{
        grid-template-columns: repeat(2, 1fr);
    }
};
@media(max-width: 441px){
    .cards-container{
        grid-template-columns: 1fr !important;
    }
}; */

</style>
