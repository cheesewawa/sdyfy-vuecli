<template>
            
              <div>
                <div style="display: flex">
                  <img :src="doctor.imgsrc" alt="Image 1" />

                  <div class="card-text">
                    <div style="display: flex">
                      <p class="name">
                        {{doctor.name}}
                      </p>
                      <div class="ocptntitle">
                        <p class="ocptntitletext">{{ doctor.ocptntitle }}</p>
                      </div>
                    </div>
                    <p class="specialties">
                      专业特长：{{ doctor.specialties }}
                    </p>
                    <p class="introduction">
                      医生简介：{{ doctor.introduction }}
                    </p>
                  </div>
                </div>
                <div class="seemore"><a href="#">查看更多></a></div>
              </div>
            
          
</template>

<script>
import { defineComponent } from '@vue/composition-api'


export default defineComponent({
    props:{
        doctor:{
          Type : Object,
        }
    },
    setup() {
        
    },
})
</script>

