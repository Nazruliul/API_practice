<script setup>
import {ref, onMounted} from 'vue'

const books = ref([])
const title = ref('')
const description = ref('')

const fetchBooks = async() =>{
    try{ 
        const res = await fetch("https://jsonplaceholder.typicode.com/posts")
        const data =  await res.json()
        books.value = data.slice(0,10)
    }catch(error){
        console.log('error', error)
    }
}

onMounted(() => {
    fetchBooks()
})
</script>
 <template>
    <div>
        <h1 class="text-center">Data buku</h1>
        <div class="container m-4">

            <div class="row">
                
                        <div class="col-sm-5 mb-4 margin-auto my-4 mx-4" v-for="book in books" :key="book.id">
                        <div class="card h-100 shadow-sm">
                            <div class="card-body flex-column">
                                <h3>{{ book.title }}</h3>
                                <p>{{ book.body }}</p>
                                <a href="#" class="btn btn-primary mt-1">Go somewhere</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            </div>
   

 </template>