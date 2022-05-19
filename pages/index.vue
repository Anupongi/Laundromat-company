<template>
  <div>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <v-card>
          <h2 class="head-line">LAUNDROMAT COMPANY</h2>
          <v-card-text>
            <p style="color:black;font-size:18px">กรุณาเลือกเครื่องที่คุณต้องการใช้บริการและหยอดเหรียญ</p>
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
          <img src="@/assets/washing-machines.png" alt="" class="washing"  @click="dialog2 = true"/>
          <v-card-text>
            <h5>เครื่องที่ 2</h5>
            <div style="display: flex">
              <b>สถานะการซัก :</b>
              <div id="ten-countdown2" class="ten-countdown"></div>
            </div>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12" sm="8" md="4">
        <v-card>
          <img src="@/assets/washing-machines.png" alt="" class="washing" @click="dialog3 = true" />
          <v-card-text>
            <h5>เครื่องที่ 3</h5>
            <div style="display: flex">
              <b>สถานะการซัก :</b>
              <div id="ten-countdown3" class="ten-countdown"></div>
            </div>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>

    <v-dialog v-model="dialog" width="700">
      <v-card>
        <h2 class="head-line grey lighten-2">กรุณาหยอดเหรียญ</h2>

        <v-card-text>
          <v-form id="input-coin" ref="form">
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
                  class="input-coin"
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
                  class="input-coin"
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
                  class="input-coin"
                ></v-text-field>
              </v-col>
            </v-row>
          </v-form>
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
    <v-dialog v-model="dialog2" width="700">
      <v-card>
        <h2 class="head-line grey lighten-2">กรุณาหยอดเหรียญ</h2>

        <v-card-text>
          <v-form id="input-coin" ref="form">
            <v-row>
              <v-col cols="12" sm="8" md="4">
                <img src="@/assets/coin_10.svg" alt="" class="coin" />
                <v-checkbox
                  v-model="checkboxC4"
                  label="เหรียญ 10 บาท"
                  class="check-coin"
                ></v-checkbox>
                <v-text-field
                  v-if="checkboxC4 == true"
                  label="จำนวน"
                  placeholder="กรุณาระบุจำนวณเหรียญ"
                  outlined
                  v-model="coinC4"
                  class="input-coin"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="8" md="4">
                <img src="@/assets/coin_5.svg" alt="" class="coin" />
                <v-checkbox
                  v-model="checkboxC5"
                  label="เหรียญ 5 บาท"
                  class="check-coin"
                ></v-checkbox>
                <v-text-field
                  v-if="checkboxC5 == true"
                  v-model="coinC5"
                  label="จำนวน"
                  placeholder="กรุณาระบุจำนวณเหรียญ"
                  outlined
                  class="input-coin"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="8" md="4">
                <img src="@/assets/coin_1.svg" alt="" class="coin" />
                <v-checkbox
                  class="check-coin"
                  v-model="checkboxC6"
                  label="เหรียญ 1 บาท"
                ></v-checkbox>
                <v-text-field
                  v-if="checkboxC6 == true"
                  v-model="coinC6"
                  label="จำนวน"
                  placeholder="กรุณาระบุจำนวณเหรียญ"
                  outlined
                  class="input-coin"
                ></v-text-field>
              </v-col>
            </v-row>
          </v-form>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            depressed
            @click="calculate2"
            v-if="checkboxC4 || checkboxC5 || checkboxC6"
          >
            เริ่มการทำงาน
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <v-dialog v-model="dialog3" width="700">
      <v-card>
        <h2 class="head-line grey lighten-2">กรุณาหยอดเหรียญ</h2>

        <v-card-text>
          <v-form id="input-coin" ref="form">
            <v-row>
              <v-col cols="12" sm="8" md="4">
                <img src="@/assets/coin_10.svg" alt="" class="coin" />
                <v-checkbox
                  v-model="checkboxC7"
                  label="เหรียญ 10 บาท"
                  class="check-coin"
                ></v-checkbox>
                <v-text-field
                  v-if="checkboxC7 == true"
                  label="จำนวน"
                  placeholder="กรุณาระบุจำนวณเหรียญ"
                  outlined
                  v-model="coinC7"
                  class="input-coin"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="8" md="4">
                <img src="@/assets/coin_5.svg" alt="" class="coin" />
                <v-checkbox
                  v-model="checkboxC8"
                  label="เหรียญ 5 บาท"
                  class="check-coin"
                ></v-checkbox>
                <v-text-field
                  v-if="checkboxC8 == true"
                  v-model="coinC8"
                  label="จำนวน"
                  placeholder="กรุณาระบุจำนวณเหรียญ"
                  outlined
                  class="input-coin"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="8" md="4">
                <img src="@/assets/coin_1.svg" alt="" class="coin" />
                <v-checkbox
                  class="check-coin"
                  v-model="checkboxC9"
                  label="เหรียญ 1 บาท"
                ></v-checkbox>
                <v-text-field
                  v-if="checkboxC9 == true"
                  v-model="coinC9"
                  label="จำนวน"
                  placeholder="กรุณาระบุจำนวณเหรียญ"
                  outlined
                  class="input-coin"
                ></v-text-field>
              </v-col>
            </v-row>
          </v-form>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            depressed
            @click="calculate3"
            v-if="checkboxC7 || checkboxC8 || checkboxC9"
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
      dialog2: false,
      dialog3: false,
      checkboxC1: false,
      coinC1: '',
      totalcoinC1: 0,
      checkboxC2: false,
      coinC2: '',
      totalcoinC2: 0,
      checkboxC3: false,
      coinC3: '',
      totalcoinC3: 0,

      checkboxC4: false,
      coinC4: '',
      totalcoinC4: 0,
      checkboxC5: false,
      coinC5: '',
      totalcoinC5: 0,
      checkboxC6: false,
      coinC6: '',
      totalcoinC6: 0,

      checkboxC7: false,
      coinC7: '',
      totalcoinC7: 0,
      checkboxC8: false,
      coinC8: '',
      totalcoinC8: 0,
      checkboxC9: false,
      coinC9: '',
      totalcoinC9: 0,
    }
  },
  watch: {
    coinC1() {
      this.totalcoinC1 = 10 * this.coinC1
      if (this.totalcoinC1 > 30) {
        Swal.fire({
          icon: 'error',
          title: 'ยอดเงินเกินกว่าที่กำหนด',
          showConfirmButton: false,
          timer: 1500,
        })
        this.$refs.form.reset()
      }
    },
    coinC2() {
      this.totalcoinC2 = 5 * this.coinC2
      if (this.totalcoinC2 > 30) {
        Swal.fire({
          icon: 'error',
          title: 'ยอดเงินเกินกว่าที่กำหนด',
          showConfirmButton: false,
          timer: 1500,
        })
        this.$refs.form.reset()
      }
    },
    coinC3() {
      this.totalcoinC3 = 1 * this.coinC3
      if (this.totalcoinC3 > 30) {
        Swal.fire({
          icon: 'error',
          title: 'ยอดเงินเกินกว่าที่กำหนด',
          showConfirmButton: false,
          timer: 1500,
        })
        this.$refs.form.reset()
      }
    },
    coinC4() {
      this.totalcoinC4 = 10 * this.coinC4
      if (this.totalcoinC4 > 30) {
        Swal.fire({
          icon: 'error',
          title: 'ยอดเงินเกินกว่าที่กำหนด',
          showConfirmButton: false,
          timer: 1500,
        })
        this.$refs.form.reset()
      }
    },
    coinC5() {
      this.totalcoinC5 = 5 * this.coinC5
      if (this.totalcoinC5 > 30) {
        Swal.fire({
          icon: 'error',
          title: 'ยอดเงินเกินกว่าที่กำหนด',
          showConfirmButton: false,
          timer: 1500,
        })
        this.$refs.form.reset()
      }
    },
    coinC6() {
      this.totalcoinC6 = 1 * this.coinC6
      if (this.totalcoinC6 > 30) {
        Swal.fire({
          icon: 'error',
          title: 'ยอดเงินเกินกว่าที่กำหนด',
          showConfirmButton: false,
          timer: 1500,
        })
        this.$refs.form.reset()
      }
    },
    coinC7() {
      this.totalcoinC7 = 10 * this.coinC7
      if (this.totalcoinC7 > 30) {
        Swal.fire({
          icon: 'error',
          title: 'ยอดเงินเกินกว่าที่กำหนด',
          showConfirmButton: false,
          timer: 1500,
        })
        this.$refs.form.reset()
      }
    },
    coinC8() {
      this.totalcoinC8 = 5 * this.coinC8
      if (this.totalcoinC8 > 30) {
        Swal.fire({
          icon: 'error',
          title: 'ยอดเงินเกินกว่าที่กำหนด',
          showConfirmButton: false,
          timer: 1500,
        })
        this.$refs.form.reset()
      }
    },
    coinC9() {
      this.totalcoinC9 = 1 * this.coinC9
      if (this.totalcoinC9 > 30) {
        Swal.fire({
          icon: 'error',
          title: 'ยอดเงินเกินกว่าที่กำหนด',
          showConfirmButton: false,
          timer: 1500,
        })
        this.$refs.form.reset()
      }
    },
  },
  methods: {
    calculate() {
      var calculate = this.totalcoinC1 + this.totalcoinC2 + this.totalcoinC3
      if (calculate != 0) {
        this.dialog = false

        if (calculate > 30) {
          Swal.fire({
            icon: 'error',
            title: 'ยอดเงินเกินกว่าที่กำหนด',
            showConfirmButton: false,
            timer: 1500,
          })
        } else if (calculate != 30) {
          Swal.fire({
            icon: 'error',
            title: 'ยอดเงินไม่พอ',
            showConfirmButton: false,
            timer: 1500,
          })
          this.dialog = true
          this.$refs.form.reset()
        } else {
          function countdown(elementName, minutes, seconds) {
            var element, endTime, hours, mins, sec, msLeft, time

            function twoDigits(n) {
              return n <= 9 ? '0' + n : n
            }

            function updateTimer() {
              msLeft = endTime - +new Date()
              if (msLeft < 1000) {
                element.innerHTML =
                  '<span style="color:green">' +
                  'หมดเวลาแล้ว! การซักเสร็จสมบูรณ์' +
                  '</span>'
                
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
          this.$refs.form.reset();
        }
      } else {
        Swal.fire({
          icon: 'error',
          title: 'ไม่พบเหรียญ',
          showConfirmButton: false,
          timer: 1500,
        })
      }
    },
    calculate2() {
      var calculate = this.totalcoinC4 + this.totalcoinC5 + this.totalcoinC6
      if (calculate != 0) {
        this.dialog2 = false

        if (calculate > 30) {
          Swal.fire({
            icon: 'error',
            title: 'ยอดเงินเกินกว่าที่กำหนด',
            showConfirmButton: false,
            timer: 1500,
          })
        } else if (calculate != 30) {
          Swal.fire({
            icon: 'error',
            title: 'ยอดเงินไม่พอ',
            showConfirmButton: false,
            timer: 1500,
          })
          this.dialog2 = true
          this.$refs.form.reset()
        } else {
          function countdown(elementName, minutes, seconds) {
            var element, endTime, hours, mins, sec, msLeft, time

            function twoDigits(n) {
              return n <= 9 ? '0' + n : n
            }

            function updateTimer() {
              msLeft = endTime - +new Date()
              if (msLeft < 1000) {
                element.innerHTML =
                  '<span style="color:green">' +
                  'หมดเวลาแล้ว! การซักเสร็จสมบูรณ์' +
                  '</span>'
                
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

          countdown('ten-countdown2', 1, 0)
          this.$refs.form.reset();
        }
      } else {
        Swal.fire({
          icon: 'error',
          title: 'ไม่พบเหรียญ',
          showConfirmButton: false,
          timer: 1500,
        })
      }
    },
    calculate3() {
      var calculate = this.totalcoinC7 + this.totalcoinC8 + this.totalcoinC9
      if (calculate != 0) {
        this.dialog3 = false

        if (calculate > 30) {
          Swal.fire({
            icon: 'error',
            title: 'ยอดเงินเกินกว่าที่กำหนด',
            showConfirmButton: false,
            timer: 1500,
          })
        } else if (calculate != 30) {
          Swal.fire({
            icon: 'error',
            title: 'ยอดเงินไม่พอ',
            showConfirmButton: false,
            timer: 1500,
          })
          this.dialog3 = true
          this.$refs.form.reset()
        } else {
          function countdown(elementName, minutes, seconds) {
            var element, endTime, hours, mins, sec, msLeft, time

            function twoDigits(n) {
              return n <= 9 ? '0' + n : n
            }

            function updateTimer() {
              msLeft = endTime - +new Date()
              if (msLeft < 1000) {
                element.innerHTML =
                  '<span style="color:green">' +
                  'หมดเวลาแล้ว! การซักเสร็จสมบูรณ์' +
                  '</span>'
                
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

          countdown('ten-countdown3', 1, 0)
          this.$refs.form.reset();
        }
      } else {
        Swal.fire({
          icon: 'error',
          title: 'ไม่พบเหรียญ',
          showConfirmButton: false,
          timer: 1500,
        })
      }
    },
  },
}
</script>
