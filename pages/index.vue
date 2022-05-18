<template>
  <div>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <v-card>
          <h2 class="head-line">LAUNDROMAT COMPANY</h2>
          <v-card-text>
            <p>กรุณาเลือกใช้เครื่องที่คุณต้องการใช้บริการ</p>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" sm="8" md="4">
        <v-card>
          <img
            src="@/assets/washing-machines.png"
            alt=""
            class="washing"
            @click="dialog = true"
          />
          <v-card-text>
            <h5>เครื่องที่ 1</h5>
            <div style="display: flex">
              <b>สถานะการซัก :</b>
              <div id="ten-countdown" class="ten-countdown"></div>
            </div>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12" sm="8" md="4">
        <v-card>
          <img src="@/assets/washing-machines.png" alt="" class="washing" />
          <v-card-text>
            <p>เครื่องที่ 4</p>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12" sm="8" md="4">
        <v-card>
          <img src="@/assets/washing-machines.png" alt="" class="washing" />
          <v-card-text>
            <p>เครื่องที่ 3</p>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>

    <v-dialog v-model="dialog" width="700">
      <v-card>
        <h2 class="head-line grey lighten-2">กรุณาหยอดเหรียญ</h2>

        <v-card-text>
          <v-row>
            <v-col cols="12" sm="8" md="4">
              <img src="@/assets/coin_10.svg" alt="" class="coin" />
              <v-checkbox
                v-model="checkboxC1"
                label="เหรียญ 10 บาท"
                class="check-coin"
              ></v-checkbox>
              <v-text-field
                v-if="checkboxC1 == true"
                label="จำนวน"
                placeholder="กรุณาระบุจำนวณเหรียญ"
                outlined
                v-model="coinC1"
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="8" md="4">
              <img src="@/assets/coin_5.svg" alt="" class="coin" />
              <v-checkbox
                v-model="checkboxC2"
                label="เหรียญ 5 บาท"
                class="check-coin"
              ></v-checkbox>
              <v-text-field
                v-if="checkboxC2 == true"
                v-model="coinC2"
                label="จำนวน"
                placeholder="กรุณาระบุจำนวณเหรียญ"
                outlined
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="8" md="4">
              <img src="@/assets/coin_1.svg" alt="" class="coin" />
              <v-checkbox
                class="check-coin"
                v-model="checkboxC3"
                label="เหรียญ 1 บาท"
              ></v-checkbox>
              <v-text-field
                v-if="checkboxC3 == true"
                v-model="coinC3"
                label="จำนวน"
                placeholder="กรุณาระบุจำนวณเหรียญ"
                outlined
              ></v-text-field>
            </v-col>
          </v-row>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            depressed
            @click="calculate"
            v-if="checkboxC1 || checkboxC2 || checkboxC3"
          >
            เริ่มการทำงาน
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import moment from 'moment'
import Swal from 'sweetalert2'
export default {
  name: 'IndexPage',
  data() {
    return {
      dialog: false,
      checkboxC1: false,
      coinC1: '',
      totalcoinC1: 0,
      checkboxC2: false,
      coinC2: '',
      totalcoinC2: 0,
      checkboxC3: false,
      coinC3: '',
      totalcoinC3: 0,
    }
  },
  watch: {
    coinC1() {
      this.totalcoinC1 = 10 * this.coinC1
      if (this.totalcoinC1 > 30) {
        console.log('ยอดเงินเกินกว่าที่กำหนด')
      }
    },
    coinC2() {
      this.totalcoinC2 = 5 * this.coinC2
      if (this.totalcoinC2 > 30) {
        console.log('ยอดเงินเกินกว่าที่กำหนด')
      }
    },
    coinC3() {
      this.totalcoinC3 = 1 * this.coinC3
      if (this.totalcoinC3 > 30) {
        console.log('ยอดเงินเกินกว่าที่กำหนด')
      }
    },
  },
  methods: {
    calculate() {
      var calculate = this.totalcoinC1 + this.totalcoinC2 + this.totalcoinC3
      // console.log(this.totalcoinC1);
      // console.log(this.totalcoinC2);
      // console.log(this.totalcoinC3);
      // console.log(calculate);
      if (calculate != 0) {
        this.dialog = false

        if (calculate > 30) {
          console.log('ยอดเงินเกินกว่าที่กำหนด')
        } else {
          function countdown(elementName, minutes, seconds) {
            var element, endTime, hours, mins, sec, msLeft, time

            function twoDigits(n) {
              return n <= 9 ? '0' + n : n
            }

            function updateTimer() {
              msLeft = endTime - +new Date()
              if (msLeft < 1000) {
                element.innerHTML = '<span style="color:green">'+'หมดเวลาแล้ว! การซักเสร็จสมบูรณ์'+ "</span>"
              } else {
                time = new Date(msLeft)
                hours = time.getUTCHours()
                mins = time.getUTCMinutes()
                sec = time.getUTCSeconds()
                if (sec == 10) {
                  const Toast = Swal.mixin({
                    toast: true,
                    position: 'top-end',
                    showConfirmButton: false,
                    timer: 1000,
                    timerProgressBar: true,
                    didOpen: (toast) => {
                      toast.addEventListener('mouseenter', Swal.stopTimer)
                      toast.addEventListener('mouseleave', Swal.resumeTimer)
                    },
                  })

                  Toast.fire({
                    icon: 'success',
                    title: 'เครื่องซักผ้าใกล้ดำเนินการสำเร็จ',
                  })
                  // element.innerHTML = 'ใกล้หมดเวลาแล้ว!'
                } else {
                  element.innerHTML =
                    (hours ? hours + ':' + twoDigits(mins) : mins) +
                    ':' +
                    twoDigits(sec)
                }

                setTimeout(updateTimer, time.getUTCMilliseconds() + 500)
              }
            }

            element = document.getElementById(elementName)
            endTime = +new Date() + 1000 * (60 * minutes + seconds) + 500
            updateTimer()
          }

          countdown('ten-countdown', 1, 0)
        }
      } else {
        console.log('ไม่พบเหรียญ')
      }
    },
  },
}
</script>
