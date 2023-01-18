<template>
  <navbar />
  <div>
    <h1>Isi Absen</h1>
    <form @submit.prevent="simpan()">
      <input v-model="tanggal" placeholder="tanggal" /> <br />
      <input v-model="nama" placeholder="nama" /> <br />
      <input v-model="keterangan" placeholder="keterangan" /> <br />
      <input v-model="matpel" placeholder="matpel" /> <br />
      <button type="submit">Simpan</button>
      <NuxtLink to="/">Kembali</NuxtLink>
    </form>
  </div>
</template>

<script setup>


const supabase = useSupabaseClient();
const tanggal = ref();
const nama = ref();
const keterangan = ref();
const matpel = ref();

async function simpan() {
  await supabase.from("kehadiran").insert({
    tanggal: tanggal.value,
    nama: nama.value,
    keterangan: keterangan.value,
    matpel: matpel.value,
  });
  navigateTo("/");
}
</script>
