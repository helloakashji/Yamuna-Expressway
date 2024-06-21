<script setup>
import { onUnmounted, onMounted, reactive, ref, watch } from 'vue';
// import { ProductService } from '@/service/ProductService';
import { useLayout } from '@/layout/composables/layout';
import Carousel from 'primevue/carousel';

const { isDarkTheme } = useLayout();


const galleryImages = ref([
    '../assets/img/gallery/bg-1.jpg',
    '../assets/img/gallery/new1-1.jpg',
    '../assets/img/gallery/Picture4-1.jpg',
]);

const images = [
      { src: '../assets/img/gallery/bg-1.jpg', alt: 'bg-1.jpg' },
      { src: '../assets/img/gallery/new1-1.jpg', alt: 'new1-1.jpg' },
      { src: '../assets/img/gallery/Picture4-1.jpg', alt: 'Picture4-1.jpg' }
    ];

    // State variables
    const currentIndex = ref(0);
    const currentImage = ref(images[currentIndex.value].src);
    const currentImageAlt = ref(images[currentIndex.value].alt);

    // Automatic carousel logic
    let intervalId = null;

    const startCarousel = () => {
      intervalId = setInterval(() => {
        currentIndex.value = (currentIndex.value + 1) % images.length;
        currentImage.value = images[currentIndex.value].src;
        currentImageAlt.value = images[currentIndex.value].alt;
      }, 3000); // Change image every 3 seconds (adjust as needed)
    };

    const stopCarousel = () => {
      clearInterval(intervalId);
    };

    onMounted(() => {
      startCarousel();
    });

    onUnmounted(() => {
      stopCarousel();
    });

const notifications = ref([
  {
    id: 1,
    title: 'New Update Available',
    time: '1 hour ago',
    content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris sed arcu id purus ultricies dictum.',
  },
  {
    id: 2,
    title: 'Important Announcement',
    time: '3 hours ago',
    content: 'Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.',
  },
  {
    id: 3,
    title: 'Scheduled Maintenance',
    time: 'Yesterday',
    content: 'Nulla facilisi. Ut euismod felis in ligula efficitur, nec posuere enim pretium.',
  },
  {
    id: 4,
    title: 'Office Closure Notice',
    time: '2 days ago',
    content: 'Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Nunc finibus nisi et consequat ullamcorper.',
  },
  {
    id: 5,
    title: 'Holiday Schedule',
    time: 'Last week',
    content: 'Nam vulputate ex ut ex blandit dapibus. Integer tincidunt pharetra neque, at ultrices urna tempus vel.',
  },
  {
    id: 6,
    title: 'Product Launch Event',
    time: 'Last month',
    content: 'Duis quis eros non erat ultrices malesuada. Fusce in odio id justo finibus malesuada sed sit amet eros.',
  },
]);




const products = ref(null);
const lineData = reactive({
    labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
    datasets: [
        {
            label: 'First Dataset',
            data: [65, 59, 80, 81, 56, 55, 40],
            fill: false,
            backgroundColor: '#2f4860',
            borderColor: '#2f4860',
            tension: 0.4
        },
        {
            label: 'Second Dataset',
            data: [28, 48, 40, 19, 86, 27, 90],
            fill: false,
            backgroundColor: '#00bb7e',
            borderColor: '#00bb7e',
            tension: 0.4
        }
    ]
});
const items = ref([
    { label: 'Add New', icon: 'pi pi-fw pi-plus' },
    { label: 'Remove', icon: 'pi pi-fw pi-minus' }
]);
const lineOptions = ref(null);
// const productService = new ProductService();

// onMounted(() => {
//     productService.getProductsSmall().then((data) => (products.value = data));
// });

const formatCurrency = (value) => {
    return value.toLocaleString('en-US', { style: 'currency', currency: 'USD' });
};
const applyLightTheme = () => {
    lineOptions.value = {
        plugins: {
            legend: {
                labels: {
                    color: '#495057'
                }
            }
        },
        scales: {
            x: {
                ticks: {
                    color: '#495057'
                },
                grid: {
                    color: '#ebedef'
                }
            },
            y: {
                ticks: {
                    color: '#495057'
                },
                grid: {
                    color: '#ebedef'
                }
            }
        }
    };
};

const applyDarkTheme = () => {
    lineOptions.value = {
        plugins: {
            legend: {
                labels: {
                    color: '#ebedef'
                }
            }
        },
        scales: {
            x: {
                ticks: {
                    color: '#ebedef'
                },
                grid: {
                    color: 'rgba(160, 167, 181, .3)'
                }
            },
            y: {
                ticks: {
                    color: '#ebedef'
                },
                grid: {
                    color: 'rgba(160, 167, 181, .3)'
                }
            }
        }
    };
};

watch(
    isDarkTheme,
    (val) => {
        if (val) {
            applyDarkTheme();
        } else {
            applyLightTheme();
        }
    },
    { immediate: true }
);
</script>

<template>
    <section class="p-col-12" style="margin-bottom: 15px;">
    <div class="p-grid flex justify-content-between">
      <!-- Logo on the left -->
      <div class="p-col-6">
        <img src="../assets/img/pages/yamuna_auth_logo.png" alt="logo" class="p-shadow-2" />
      </div>
      <!-- Links and search on the right -->
      <div class="p-col-6 p-d-flex p-jc-end p-ai-center">
        <div class="p-d-flex p-flex-column p-jc-end p-ai-center" >
          <span class="p-input-icon-right p-mr-2" style="margin-right: 10px;">
            <i class="pi pi-search" style="margin-right: 10px;"></i>
            <input type="text" placeholder="Search Allotment Number Here" class="p-inputtext p-py-1" />
          </span>
          <router-link :to="{ name: 'booknewflat' }" class="p-button p-button-success p-py-1">
          <i class="pi pi-list-alt p-mr-1"></i> Book New Flat
        </router-link>
        </div>
      </div>
    </div>
  </section>
    <div class="grid">
        <div class="col-12 lg:col-6 xl:col-3">
            <div class="card mb-0">
                <div class="flex justify-content-between mb-3">
                    <div>
                        <span class="block text-500 font-medium mb-3">Daily Visits</span>
                        <div class="text-900 font-medium text-xl">3752</div>
                    </div>
                    <div class="flex align-items-center justify-content-center bg-blue-100 border-round" style="width: 2.5rem; height: 2.5rem">
                        <i class="pi pi-map-marker text-blue-500 text-xl"></i>
                    </div>
                </div>
                <span class="text-green-500 font-medium">24 new </span>
                <span class="text-500">visits</span>
            </div>
        </div>
        <div class="col-12 lg:col-6 xl:col-3">
            <div class="card mb-0">
                <div class="flex justify-content-between mb-3">
                    <div>
                        <span class="block text-500 font-medium mb-3">Sales Status</span>
                        <div class="text-900 font-medium text-xl">3251</div>
                    </div>
                    <div class="flex align-items-center justify-content-center bg-orange-100 border-round" style="width: 2.5rem; height: 2.5rem">
                        <i class="pi pi-shopping-cart text-orange-500 text-xl"></i>
                    </div>
                </div>
                <span class="text-green-500 font-medium">152 </span>
                <span class="text-500">since last week</span>
            </div>
        </div>
        <div class="col-12 lg:col-6 xl:col-3">
            <div class="card mb-0">
                <div class="flex justify-content-between mb-3">
                    <div>
                        <span class="block text-500 font-medium mb-3">Hits</span>
                        <div class="text-900 font-medium text-xl">28441</div>
                    </div>
                    <div class="flex align-items-center justify-content-center bg-cyan-100 border-round" style="width: 2.5rem; height: 2.5rem">
                        <i class="pi pi-chart-bar text-cyan-500 text-xl"></i>
                    </div>
                </div>
                <span class="text-green-500 font-medium">520 </span>
                <span class="text-500">newly hits</span>
            </div>
        </div>
        <div class="col-12 lg:col-6 xl:col-3">
            <div class="card mb-0">
                <div class="flex justify-content-between mb-3">
                    <div>
                        <span class="block text-500 font-medium mb-3">Subscribers</span>
                        <div class="text-900 font-medium text-xl">1252</div>
                    </div>
                    <div class="flex align-items-center justify-content-center bg-purple-100 border-round" style="width: 2.5rem; height: 2.5rem">
                        <i class="pi pi-users text-purple-500 text-xl"></i>
                    </div>
                </div>
                <span class="text-green-500 font-medium">85 </span>
                <span class="text-500">since last week</span>
            </div>
        </div>

        <div class="col-12 xl:col-8">
            <div class="card">
                <!-- <img :src="currentImage" :alt="currentImageAlt" /> -->
                <img src="../assets/img/gallery/bg-1.jpg" alt="bg-1.jpg" srcset="">
                <img src="../assets/img/gallery/new1-1.jpg" alt="bg-1.jpg" srcset="">
                <img src="../assets/img/gallery/Picture4-1.jpg" alt="bg-1.jpg" srcset="">
  </div>
   <!-- <div class="flex justify-between">
      <div class="card">
        <p>
          Lorem ipsum dolor sit amet consectetur, adipisicing elit. Magni pariatur obcaecati 
        </p>
      </div>
      <div class="card">
        <p>
          Lorem ipsum dolor sit amet consectetur, adipisicing elit. Magni pariatur obcaecati atque nesciunt officiis 
        </p>
      </div>
    </div> -->

    <!-- <div class="card">
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis odio veritatis impedit voluptas dignissimos atque quo num
      </p>
    </div> -->
        </div>
        <div class="col-12 xl:col-4">
            <div class="card">
    <div class="">
      <h5>Public Announcements</h5>
    </div>
      <div v-for="notification in notifications" :key="notification.id" class="card p-shadow-2 card-bg-light">
        <div class="flex align-items-center justify-content-between">
          <h6>{{ notification.title }}</h6>
          <span class="text-grey text-small">{{ notification.time }}</span>
        </div>
        <p class="text-regular">{{ notification.content }}</p>
      </div>
  </div>
        </div>
        
    </div>
</template>
<style scoped>
.card {
  overflow: hidden; /* Hide any content that overflows the card */
  position: relative; /* Establish positioning context */
}

.card img {
  width: 100%; /* Make the image width 100% of its parent (the card) */
  height: 100%; /* Make the image height 100% of its parent (the card) */
  object-fit: cover; /* Scale the image while maintaining aspect ratio to cover the entire container */
  object-position: center; /* Center the image within its container */
}

/* .card-bg-light {
    background: #fff0e7;
    &.dark-theme {
        background: var(--dark-surface-card);
    }
} */

</style>

<!-- <style scoped>
.notification-cards {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.notification-card {
  padding: 20px;
  border-radius: 8px;
  background-color: #ffffff;
  /* box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); */
  box-shadow: 0 1px 6px rgba(0, 0, 0, 0.175);
  border: 1px solid #d4d4d4 ;
}

.notification-card h6 {
  font-size: 14px;
  font-weight: bold;
  margin-bottom: 10px;
}

.notification-card .text-small {
  font-size: 11px;
  color: #999999;
}

.notification-card .text-regular {
  font-size: 14px;
  line-height: 1.5;
}
</style> -->