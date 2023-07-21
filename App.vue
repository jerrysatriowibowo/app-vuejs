<template>
  <div>
    <h2>Formulir</h2>
    <form @submit.prevent="submitForm">
    <label for="">Nama</label>
    <input type="text" name="nama" v-model="siswa.nama">
    <br>
    <label for="">Kelas</label>
    <input type="text" name="kelas" v-model="siswa.kelas">
    <br>
    <label for="">Alamat</label>
    <input type="text" name="alamat" v-model="siswa.alamat">
    <br>
    <label for="">Nilai Mtk</label>
    <input type="number" name="mtk" v-model="siswa.mtk">
    <br>
    <label for="">Nilai Bhs Indo</label>
    <input type="number" name="indo" v-model="siswa.indo">
    <br>
    <label for="">Nilai Ipa</label>
    <input type="number" name="ipa" v-model="siswa.ipa">
    <br>
    <button type="submit">Simpan</button>
  </form>
  <div v-if="showResult">
    nama       : {{ name }}<br>
    kelas      : {{ kelas }}<br>
    alamat     : {{ alamat }}<br>
    nilai mtk  : {{ mtk }}<br>
    nilai indo : {{ indo }}<br>
    nilai ipa  : {{ ipa }}<br>
    Total nilai: {{ total }}<br>
    Keterangan : {{ keterangan }}
  </div>
  </div>
</template>
<script>
import { ref } from 'vue';

export default {
  name: 'MyComponent',
  data() {
    return {
      siswa : { 
        nama:'',
        kelas:'',
        alamat:'',
        mtk:'',
        indo:'',
        ipa:''
      },
      showResult: ref(false),
      name: ref(''),
      kelas: ref(''),
      alamat: ref(''),
      mtk: ref(''),
      indo: ref(''),
      ipa: ref(''),
      total: 0,
      keterangan: ref('')
    }
  },
    methods: {
      submitForm(){
        this.name = this.siswa.nama,
        this.kelas = this.siswa.kelas,
        this.alamat = this.siswa.alamat,
        this.mtk = this.siswa.mtk,
        this.indo = this.siswa.indo,
        this.ipa = this.siswa.ipa,
        this.total = parseInt(this.siswa.mtk) + parseInt(this.siswa.indo) + parseInt(this.siswa.ipa)
        if(this.total > 240) {
          this.keterangan = 'Lulus'
        } else {
          this.keterangan = 'Remedial'
        }
        this.showResult = true
        }
      },
    };
</script>
<style>
h2{
  color: blue;
}
</style>