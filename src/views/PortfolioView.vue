<script>
export default {
  data() {
    return {
      activeTab: 1,
      searchQuery: "",
      selectedTech: "All",
      items: [
        {
          id: 1,
          name: "Sistem Penjaminan Mutu Internal(SPMI)",
          imageUrl: "SPMI",
          status:
            "I designed this SPMI dashboard to simplify the management and monitoring of data related to the Internal Quality Assurance System in the institution. The goal? To continuously improve the quality of education!",
          tech: "Node.js, Tailwind",
          github: "https://github.com/adenwilgit/SPMI-Web",
          demo: "null",
        },
        {
          id: 2,
          name: "Online Shop Gartig Sply",
          imageUrl: "TokoSepatu",
          status:
            "This image shows the user interface (UI) design or the frontend of an online shoe store called (Gartig Sply). It should be noted that this is only a visual representation and is not connected to any database or backend functionality.",
          tech: "React.js, Tailwind",
          github: "https://github.com/adenwilgit/Dencode",
          demo: "null",
        },
        {
          id: 3,
          name: "Aplikasi CRUD Data Penelitian",
          imageUrl: "DataPenelitian",
          status:
            "This Research CRUD Application I developed to simplify the management and monitoring of research data within the institution. The goal is to enhance efficiency and transparency in the research process, as well as to support better decision-making!",
          tech: "Node.js, Tailwind",
          github: "https://github.com/adenwilgit/Infra-Website",
          demo: "null",
        },
        {
          id: 4,
          name: "Aplikasi Peminjaman Buku Online",
          imageUrl: "Figma",
          status:
            "This illustration showcases an example of the user interface (UI) for an online book lending application. These mockups were created in Figma, with a focus on different user experiences: the mobile view for library patrons (to search and borrow books), and the desktop view as an admin dashboard (to manage inventory and loan data). Note the design elements and layout tailored to each platform.",
          tech: "Figma",
          figma:
            "https://www.figma.com/design/EJWInJou75AzXk828NfwlF/Untitled?node-id=0-1&t=4T6qPQ1UzdWSd62J-1",
          demo: "null",
        },
        {
          id: 5,
          name: "Aplikasi Latihan Rumahan(Exercise)",
          imageUrl: "ApkExercise",
          status:
            "This is part of the design for a home workout application, specifically for UI elements such as the appbar, tabbar, and bottom bar. The exercise data itself is obtained from an external API. This application is built with Flutter and Dart.",
          tech: "Flutter, Dart",
          github: "null",
          demo: "null",
        },
        {
          id: 6,
          name: "Poster Sandfray Sando",
          imageUrl: "canvamakanan",
          status:
            "This poster aims to promote Sandfray Sando, a type of sandwich filled with fresh cream, sweet grapes, and fresh mangoes. Its purpose is to attract consumer attention and encourage them to purchase this product.",
          tech: "Canva",
          github: "null",
          demo: "null",
        },
        {
          id: 7,
          name: "Poster Buka Puasa Bersama HR",
          imageUrl: "canvabukber",
          status:
            "This poster serves as an official invitation to the breaking of the fast gathering organized by the Homeriz Family (HR) on Monday, April 11, 2023. Its purpose is to inform and invite family and relatives to attend the event.",
          tech: "Canva",
          github: "null",
          demo: "null",
        },
      ],
      isLoading: true,
    };
  },
  computed: {
    // Filter projects berdasarkan search dan teknologi
    filteredProjects() {
      return this.items.filter((item) => {
        const matchesSearch =
          item.name.toLowerCase().includes(this.searchQuery.toLowerCase()) ||
          item.status.toLowerCase().includes(this.searchQuery.toLowerCase());
        const matchesTech =
          this.selectedTech === "All" || item.tech.includes(this.selectedTech);
        return matchesSearch && matchesTech;
      });
    },
    // Get unique technologies
    technologies() {
      const techs = new Set(["All"]);
      this.items.forEach((item) => {
        item.tech.split(", ").forEach((t) => techs.add(t));
      });
      return Array.from(techs);
    },
  },
  mounted() {
    // Simulate loading
    setTimeout(() => {
      this.isLoading = false;
    }, 1000);
  },
};
</script>
<template>
  <div class="px-5 py-5 md:px-12 md:py-10 text-left text-amber-50 mx-3">
    <article data-page="about">
      <header>
        <div
          class="text-2xl font-bold text-white mb-10 fadein-bot title-section flex items-center justify-center flex-col"
        >
          <!-- <div class="h-[1px] w-10 bg-amber-200 md:w-20 aos-init aos-animate"></div> -->
          <h4>Past Project Experience</h4>
          <h4
            class="text-base font-normal text-transparent bg-clip-text bg-gradient-to-r from-slate-100 to-amber-300"
          >
            Explore the projects I've worked on so far
          </h4>
        </div>
      </header>
      <section>
        <div
          class="mb-8 flex flex-col md:flex-row gap-4 justify-between items-center"
        >
          <input
            v-model="searchQuery"
            type="text"
            placeholder="Search projects..."
            class="w-full md:w-64 px-4 py-2 rounded-lg bg-[#1e1e1f] border border-[#383838] text-amber-50 focus:outline-none focus:border-amber-300"
          />

          <div class="flex gap-2 flex-wrap justify-center">
            <button
              v-for="tech in technologies"
              :key="tech"
              @click="selectedTech = tech"
              :class="[
                'px-3 py-1 rounded-full text-sm transition-all',
                selectedTech === tech
                  ? 'bg-amber-300 text-black'
                  : 'bg-[#1e1e1f] text-amber-50 hover:bg-[#282828]',
              ]"
            >
              {{ tech }}
            </button>
          </div>
        </div>

        <div>
          <div
            class="grid grid-cols-1 gap-4 pb-32 md:grid-cols-3 md:gap-3 xl:grid-cols-3 xl:gap-3 2xl:gap-5 fade-zoom-in"
          >
            <!-- Loading skeleton -->
            <template v-if="isLoading">
              <div v-for="n in 6" :key="n" class="animate-pulse">
                <div
                  class="item-card flex flex-col items-center gap-2 rounded bg-[#1e1e1f] border border-[#383838] rounded-xl px-5 py-5"
                >
                  <div class="bg-gray-700 h-48 w-full rounded-xl"></div>
                  <div class="w-full space-y-3">
                    <div class="h-4 bg-gray-700 rounded"></div>
                    <div class="h-3 bg-gray-700 rounded w-2/3"></div>
                    <div class="h-3 bg-gray-700 rounded w-1/2"></div>
                  </div>
                </div>
              </div>
            </template>

            <!-- Actual content -->
            <template v-else>
              <div v-for="item in filteredProjects" :key="item.id">
                <div
                  class="item-card flex flex-col items-center gap-2 rounded bg-[#1e1e1f] hover:bg-[#282828] border border-[#383838] rounded-xl text-amber-50 md:gap-3 px-5 py-5 lg:px-5"
                >
                  <div
                    class="flex h-12 w-12 items-center justify-center p-0 h-full w-full lg:p-0 zoom-in"
                  >
                    <img
                      alt="HTML"
                      loading="lazy"
                      decoding="async"
                      data-nimg="1"
                      class="drop-shadow-xl rounded rounded-xl"
                      :src="'/img/portfolio-' + item.imageUrl + '.png'"
                    />
                  </div>
                  <div
                    class="w-full flex flex-col gap-2 items-center text-sm md:text-base lg:text-lg"
                  >
                    <div class="title-text font-medium text-secondary">
                      {{ item.name }}
                    </div>
                    <div
                      class="w-full text-left text-[10px] text-[#c1c1c1] md:text-xs lg:text-sm"
                    >
                      {{ item.status }}
                    </div>
                    <div
                      class="w-full mt-4 text-normal text-sm text-left text-amber-200"
                    >
                      {{ item.tech }}
                    </div>
                    <div class="w-full flex justify-end">
                      <div
                        class="flex cursor-pointer items-end gap-2 text-primary"
                      >
                        <!-- Jika ada figma link -->
                        <a
                          v-if="item.figma"
                          :href="item.figma"
                          target="_blank"
                          rel="noreferrer"
                          title="View Figma project"
                          class="transition-all hover:scale-110"
                        >
                          <!-- SVG Figma Berwarna -->
                          <svg
                            width="18"
                            height="18"
                            viewBox="0 0 24 24"
                            fill="none"
                            xmlns="http://www.w3.org/2000/svg"
                          >
                            <g clip-path="url(#clip0_87_12)">
                              <path
                                d="M5 12C5 10.3431 6.34315 9 8 9H11V15H8C6.34315 15 5 13.6569 5 12Z"
                                fill="#1ABCFE"
                              />
                              <path
                                d="M5 6C5 4.34315 6.34315 3 8 3H11V9H8C6.34315 9 5 7.65685 5 6Z"
                                fill="#0ACF83"
                              />
                              <path
                                d="M11 3H14C15.6569 3 17 4.34315 17 6C17 7.65685 15.6569 9 14 9H11V3Z"
                                fill="#FF7262"
                              />
                              <path
                                d="M17 12C17 13.6569 15.6569 15 14 15C12.3431 15 11 13.6569 11 12C11 10.3431 12.3431 9 14 9C15.6569 9 17 10.3431 17 12Z"
                                fill="#F24E1E"
                              />
                              <path
                                d="M11 15H8C6.34315 15 5 16.3431 5 18C5 19.6569 6.34315 21 8 21C9.65685 21 11 19.6569 11 18V15Z"
                                fill="#A259FF"
                              />
                            </g>
                            <defs>
                              <clipPath id="clip0_87_12">
                                <rect
                                  width="12"
                                  height="18"
                                  fill="white"
                                  transform="translate(5 3)"
                                />
                              </clipPath>
                            </defs>
                          </svg>
                        </a>

                        <a
                          v-if="item.github !== 'null' && !item.figma"
                          :href="item.github"
                          target="_blank"
                          rel="noreferrer"
                          title="View github repository"
                          class="transition-all hover:text-accent"
                        >
                          <svg
                            stroke="currentColor"
                            fill="none"
                            stroke-width="2"
                            viewBox="0 0 24 24"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            height="16"
                            width="16"
                            xmlns="http://www.w3.org/2000/svg"
                          >
                            <path
                              d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"
                            ></path></svg
                        ></a>
                        <a
                          v-if="item.demo !== 'null'"
                          :href="item.demo"
                          target="_blank"
                          rel="noreferrer"
                          title="View finished project"
                          class="transition-all hover:text-accent"
                        >
                          <svg
                            stroke="currentColor"
                            fill="none"
                            stroke-width="2"
                            viewBox="0 0 24 24"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            height="18"
                            width="18"
                            xmlns="http://www.w3.org/2000/svg"
                          >
                            <path
                              d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"
                            ></path>
                            <polyline points="15 3 21 3 21 9"></polyline>
                            <line x1="10" y1="14" x2="21" y2="3"></line></svg
                        ></a>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </template>
          </div>
        </div>
      </section>
    </article>
  </div>
</template>

<style>
.item-card:hover {
  transition: transform 0.3s ease;
  transform: translateY(-8px);
}
svg:hover {
  stroke: #ffdb70;
}
@keyframes fadeZoomIn {
  0% {
    opacity: 0;
    transform: scale(0.5);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}

/* Menggunakan animasi pada elemen yang diinginkan */
.fade-zoom-in {
  animation: fadeZoomIn 1s ease-in-out;
}

.item-card {
  position: relative;
  overflow: hidden;
}

.item-card::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    120deg,
    transparent,
    rgba(255, 219, 112, 0.1),
    transparent
  );
  transition: 0.5s;
}

.item-card:hover::before {
  left: 100%;
}

/* Loading animation */
@keyframes pulse {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

.animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}
</style>
