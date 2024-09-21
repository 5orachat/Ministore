<template>
  <div>
    <div class="q-pa-md" style="max-width: 400px">
      <q-form @submit.prevent="onSubmit">
        <q-input v-model="id" label="ID" readonly />
        <q-input v-model="name" label="Product Name" />
        <q-input v-model="description" label="Description" />
        <q-input v-model="price" label="Price" type="number" />
        <q-input v-model="category" label="Category" />
        <q-input v-model="image_url" label="Image URL" />
        <q-btn type="submit" label="Update" color="primary" />
      </q-form>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useRoute, useRouter } from 'vue-router';

const route = useRoute();
const router = useRouter();

const id = ref(route.params.id);
const name = ref('');
const description = ref('');
const price = ref('');
const category = ref('');
const image_url = ref('');

// Fetch product data on component mount
const fetchData = () => {
    fetch('http://localhost:8800/api/v1/products/' + id.value)
      .then(res => res.json())
      .then((result) => {
        name.value = result.name;
        description.value = result.description;
        price.value = result.price;
        category.value = result.category;
        image_url.value = result.image_url;
      })
      .catch((error) => {
        console.error('Error fetching data:', error);
        alert('Error fetching data:', error);
      });
  };
  fetchData();
  
  // ฟังก์ชันสำหรับอัปเดตข้อมูลลูกค้า
  const onSubmit = () => {
    const myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");
  
    const raw = JSON.stringify({
      "name": name.value,
      "description": description.value,
      "price": price.value,
      "category": category.value,
      "image_url": image_url.value
    });
  
    const requestOptions = {
      method: "PUT",
      headers: myHeaders,
      body: raw,
      redirect: "follow"
    };
  
    fetch(`http://localhost:8800/api/v1/products/${id.value}`, requestOptions)
      .then((response) => {
        if(!response.ok) {
            return response.json().then((err) => {
                throw new Error(err.message || 'Something went worng!'); 
            });
        }
        return response.json()
      })
      .then((result) => {
        alert(result.message);
        console.log(result);
        if(result.status === 'ok'){
            router.push('/')

        }
        fetchData()
      })
      .catch((error) => {
        console.error('Error updating product:', error)
        alert(`Error: ${error.message}`)
    });
  };
  </script>