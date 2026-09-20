<script lang="ts">
  interface Video {
    id: string;
    category: 'informasi' | 'tutorial';
    categoryLabel: string;
    title: string;
    desc: string;
    channel: string;
    avatarText: string;
  }

  // Data senarai video IPKD
  const videos: Video[] = [
    {
      id: "Wceczbalttc",
      category: "informasi",
      categoryLabel: "Informasi",
      title: "IPKD 2026 Kualitas Kelola Menjadi Tolak Ukur APBD",
      desc: "Seberapa sehat keuangan daerahmu? Video ini mengungkap bagaimana IPKD mengukurnya dari perencanaan, belanja hingga opini BPK atas LKPD.",
      channel: "Bapperida Kota Sungai Penuh",
      avatarText: "BP"
    },
    {
      id: "kU2haM1VQl0",
      category: "informasi",
      categoryLabel: "Informasi",
      title: "Insentif Daerah dari Nilai IPKD yang Tinggi",
      desc: "Prestasi di IPKD akan dapat apresiasi di mana juara 1 mendapat Rp 3 miliar, juara 2 Rp 2 miliar, dan juara 3 Rp 1 miliar langsung ke kas daerah.",
      channel: "Bapperida Kota Sungai Penuh",
      avatarText: "BP"
    },
    {
      id: "ouxgYRqdm84",
      category: "tutorial",
      categoryLabel: "Tutorial",
      title: "Tutorial Penginputan IPKD Dimensi I 2026",
      desc: "Tutorial Lengkap IPKD Dimensi 1 Tahun 2026 secara bertahap, dari dokumen, integrasi data, pengisian template Excel, hingga unggah bukti dukung.",
      channel: "Bapperida Kota Sungai Penuh",
      avatarText: "BP"
    },
    {
      id: "xbkpyKsDy-w",
      category: "tutorial",
      categoryLabel: "Tutorial",
      title: "Tutorial Lengkap Penginputan IPKD Dimensi II (Alokasi Belanja) Tahun 2026",
      desc: "Tata cara pengisian dan penginputan data pada Dimensi II (Alokasi Belanja) dalam aplikasi IPKD secara terstruktur.",
      channel: "Bapperida Kota Sungai Penuh",
      avatarText: "BP"
    },
    {
      id: "KenghNrV_5Q",
      category: "tutorial",
      categoryLabel: "Tutorial",
      title: "Tutorial Lengkap Penginputan IPKD Dimensi III - 2026",
      desc: "Video ini menjelaskan tata cara penginputan 19 dokumen wajib, termasuk 3 indikator dokumen tambahan baru.",
      channel: "Bapperida Kota Sungai Penuh",
      avatarText: "BP"
    },
    {
      id: "FIJmJFcs9EE",
      category: "tutorial",
      categoryLabel: "Tutorial",
      title: "Tutorial Lengkap Penginputan IPKD Dimensi IV 2026",
      desc: "Penginputan data Indeks Pengelolaan Keuangan Daerah (IPKD) Capaian Kinerja secara detail dan tuntas.",
      channel: "Bapperida Kota Sungai Penuh",
      avatarText: "BK"
    },
    {
      id: "belNfJ1dvds",
      category: "tutorial",
      categoryLabel: "Tutorial",
      title: "Tutorial Lengkap Penginputan IPKD Dimensi V - 2026",
      desc: "Dijelaskan langkah demi langkah pengisian data, penentuan kapasitas fiskal daerah, dan simulasi penilaian.",
      channel: "Bapperida Kota Sungai Penuh",
      avatarText: "BP"
    },
    {
      id: "pqM_bWoZ8Uo",
      category: "tutorial",
      categoryLabel: "Tutorial",
      title: "Tutorial Lengkap Penginputan IPKD Dimensi VI - 2026",
      desc: "Panduan teknis penginputan dokumen dan pelaporan Opini BPK di IPKD hingga verifikasi akhir.",
      channel: "Bapperida Kota Sungai Penuh",
      avatarText: "BP"
    }
  ];

  // State Reaktif Runes
  let searchTerm = $state("");
  let selectedCategory = $state("all");

  // Filter video reaktif
  let filteredVideos = $derived(
    videos.filter((video) => {
      const matchesCategory =
        selectedCategory === "all" || video.category === selectedCategory;
      const query = searchTerm.toLowerCase().trim();
      const matchesSearch =
        query === "" ||
        video.title.toLowerCase().includes(query) ||
        video.desc.toLowerCase().includes(query) ||
        video.channel.toLowerCase().includes(query);

      return matchesCategory && matchesSearch;
    })
  );

  // Fallback resolusi thumbnail
  function handleImageError(event: Event, videoId: string) {
    const target = event.currentTarget as HTMLImageElement;
    if (target) {
      target.src = `https://img.youtube.com/vi/${videoId}/hqdefault.jpg`;
    }
  }
</script>

<svelte:head>
  <title>IPKD Tube 2026 • Tutorial & Informasi Pengelolaan Keuangan</title>
  <meta
    name="description"
    content="Katalog video tutorial penginputan dokumen IPKD Dimensi I hingga VI dan informasi penilaian Indeks Pengelolaan Keuangan Daerah 2026."
  />
</svelte:head>

<div class="relative min-h-screen bg-[#070b14] text-slate-100 selection:bg-sky-500/30 selection:text-sky-200 font-sans antialiased overflow-x-hidden">
  <!-- Ambient Background Glows (Deep Dark Blue / Midnight Obsidian Glows) -->
  <div class="pointer-events-none absolute inset-0 overflow-hidden">
    <div class="absolute inset-0 bg-[radial-gradient(rgba(56,189,248,0.12)_1px,transparent_1px)] [background-size:24px_24px] opacity-35"></div>
    <div class="absolute -top-36 left-1/2 -translate-x-1/2 w-[800px] sm:w-[1100px] h-[450px] bg-gradient-to-b from-sky-600/15 via-blue-700/10 to-transparent blur-[140px] rounded-full"></div>
    <div class="absolute top-[600px] -right-36 w-[550px] h-[550px] bg-blue-900/15 blur-[150px] rounded-full"></div>
  </div>

  <!-- Navigation Bar (Dark Frosted Glass with Deep Blue Border) -->
  <header class="sticky top-0 z-50 backdrop-blur-xl bg-[#070b14]/85 border-b border-slate-800/80 transition-all duration-300">
    <div class="max-w-6xl mx-auto px-6 h-16 flex items-center justify-between gap-4">
      <div class="flex items-center gap-3">
        <a
          href="/"
          class="inline-flex items-center gap-1.5 px-3 py-1.5 rounded-full text-xs font-semibold text-slate-300 hover:text-white bg-slate-900/80 hover:bg-slate-800 border border-slate-700/80 transition-colors"
        >
          <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M15 19l-7-7 7-7" />
          </svg>
          <span>Beranda</span>
        </a>
        <span class="text-slate-700">/</span>
        <div class="flex items-center gap-2">
          <div class="w-7 h-7 rounded-lg bg-gradient-to-br from-rose-500 to-red-600 text-white flex items-center justify-center text-[11px] font-black shadow-xs">
            ▶
          </div>
          <span class="text-sm font-bold tracking-tight text-white">
            IPKD Tube
          </span>
          <span class="text-[11px] font-semibold px-2.5 py-0.5 rounded-full bg-sky-950/80 border border-sky-800/80 text-sky-300">
            2026
          </span>
        </div>
      </div>

      <!-- Quick Search Bar in Header -->
      <div class="relative w-full max-w-xs hidden sm:block">
        <svg
          class="w-3.5 h-3.5 text-sky-400 absolute left-3 top-1/2 -translate-y-1/2 pointer-events-none"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
        </svg>
        <input
          type="text"
          bind:value={searchTerm}
          placeholder="Cari video IPKD..."
          class="w-full pl-8 pr-3 py-1.5 text-xs rounded-full bg-[#111c33] border border-sky-500/30 text-slate-100 placeholder:text-slate-400 focus:outline-none focus:bg-[#15233e] focus:border-sky-400 focus:ring-4 focus:ring-sky-500/25 transition-all shadow-inner"
        />
      </div>
    </div>
  </header>

  <main class="relative max-w-6xl mx-auto px-6 pt-12 pb-28 space-y-12">
    <!-- Hero Header IPKD (Dark Blue Aesthetic) -->
    <section class="max-w-3xl space-y-3 pt-2">
      <div class="inline-flex items-center gap-2 px-3.5 py-1 rounded-full text-xs font-semibold bg-sky-950/60 border border-sky-800/70 text-sky-300 shadow-2xs">
        <span class="text-sky-400 font-bold">KOLEKSI MULTIMEDIA</span>
        <span class="w-1 h-1 rounded-full bg-sky-400"></span>
        <span class="text-sky-300/90 font-medium">Bapperida Kota Sungai Penuh</span>
      </div>

      <h1 class="text-3xl sm:text-5xl font-extrabold tracking-tight text-white leading-tight">
        Katalog Video IPKD 2026
      </h1>

      <p class="text-base sm:text-lg text-slate-300 leading-relaxed font-normal">
        Himpunan video tutorial penginputan dokumen Dimensi I hingga VI serta informasi indikator penilaian Indeks Pengelolaan Keuangan Daerah.
      </p>
    </section>

    <!-- Controls: Filter & Search (Mobile Search included) -->
    <section class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 pb-4 border-b border-slate-800/80">
      <!-- Category Filter Pills (Blue Highlight) -->
      <div class="flex items-center gap-1.5 overflow-x-auto pb-1 sm:pb-0">
        <button
          type="button"
          onclick={() => (selectedCategory = "all")}
          class="px-4 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap transition-all cursor-pointer {selectedCategory ===
          'all'
            ? 'bg-gradient-to-r from-sky-500 to-blue-600 text-white shadow-sm shadow-sky-600/30'
            : 'bg-[#111c33] text-slate-300 hover:bg-[#162544] hover:text-white border border-sky-500/20'}"
        >
          Semua Video ({videos.length})
        </button>
        <button
          type="button"
          onclick={() => (selectedCategory = "informasi")}
          class="px-4 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap transition-all cursor-pointer {selectedCategory ===
          'informasi'
            ? 'bg-gradient-to-r from-sky-500 to-blue-600 text-white shadow-sm shadow-sky-600/30'
            : 'bg-[#111c33] text-slate-300 hover:bg-[#162544] hover:text-white border border-sky-500/20'}"
        >
          Informasi
        </button>
        <button
          type="button"
          onclick={() => (selectedCategory = "tutorial")}
          class="px-4 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap transition-all cursor-pointer {selectedCategory ===
          'tutorial'
            ? 'bg-gradient-to-r from-sky-500 to-blue-600 text-white shadow-sm shadow-sky-600/30'
            : 'bg-[#111c33] text-slate-300 hover:bg-[#162544] hover:text-white border border-sky-500/20'}"
        >
          Tutorial Dimensi
        </button>
      </div>

      <!-- Mobile Search Bar -->
      <div class="relative w-full sm:hidden">
        <svg
          class="w-3.5 h-3.5 text-sky-400 absolute left-3 top-1/2 -translate-y-1/2 pointer-events-none"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
        </svg>
        <input
          type="text"
          bind:value={searchTerm}
          placeholder="Cari video IPKD..."
          class="w-full pl-8 pr-4 py-2 text-xs rounded-full bg-[#111c33] border border-sky-500/30 text-slate-100 placeholder:text-slate-400 focus:outline-none focus:bg-[#15233e] focus:border-sky-400 focus:ring-4 focus:ring-sky-500/25 transition-all shadow-inner"
        />
      </div>

      <div class="text-xs text-slate-400 font-medium hidden md:block">
        Menampilkan <strong>{filteredVideos.length}</strong> video
      </div>
    </section>

    <!-- Video Cards Grid (Dark Blue Cards Kontras & Menonjol) -->
    {#if filteredVideos.length > 0}
      <section class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        {#each filteredVideos as video (video.id)}
          <article
            class="group relative rounded-3xl bg-gradient-to-b from-[#142038] via-[#101a2f] to-[#0c1527] hover:from-[#192847] hover:via-[#132039] hover:to-[#0f1a30] border-2 border-sky-500/30 hover:border-sky-400/70 p-4.5 transition-all duration-300 shadow-xl shadow-black/60 hover:shadow-2xl hover:shadow-sky-900/40 hover:-translate-y-1.5 flex flex-col justify-between overflow-hidden ring-1 ring-white/5"
          >
            <!-- Decorative Light Line -->
            <div class="pointer-events-none absolute top-0 left-0 right-0 h-1 bg-gradient-to-r from-transparent via-sky-400/70 to-transparent opacity-60 group-hover:opacity-100 transition-opacity"></div>

            <div class="space-y-3.5">
              <!-- Video Thumbnail Container -->
              <div class="relative aspect-video w-full overflow-hidden rounded-2xl bg-black border border-sky-500/20 shadow-md">
                <img
                  src="https://img.youtube.com/vi/{video.id}/maxresdefault.jpg"
                  alt={video.title}
                  onerror={(e) => handleImageError(e, video.id)}
                  class="h-full w-full object-cover transition-transform duration-500 group-hover:scale-105"
                  loading="lazy"
                />

                <!-- Category Pill Badge -->
                <span class="absolute left-2.5 top-2.5 rounded-full bg-[#0a1120]/90 backdrop-blur-md px-2.5 py-0.5 text-[11px] font-bold text-sky-300 shadow-xs border border-sky-400/30">
                  {video.categoryLabel}
                </span>

                <!-- Platform Tag -->
                <span class="absolute bottom-2.5 right-2.5 rounded-md bg-black/85 backdrop-blur-sm px-2 py-0.5 text-[10px] font-medium text-white flex items-center gap-1 border border-white/10">
                  <span class="text-rose-500">▶</span> YouTube
                </span>

                <!-- Subtle Play Icon Overlay -->
                <div class="absolute inset-0 flex items-center justify-center pointer-events-none">
                  <div class="w-11 h-11 rounded-full bg-[#1b2b4a]/90 backdrop-blur-md text-sky-300 flex items-center justify-center shadow-lg shadow-black/50 opacity-0 scale-75 group-hover:opacity-100 group-hover:scale-100 transition-all duration-300 border border-sky-400/40">
                    <svg class="w-5 h-5 ml-0.5 fill-current" viewBox="0 0 24 24">
                      <path d="M8 5v14l11-7z" />
                    </svg>
                  </div>
                </div>
              </div>

              <!-- Channel Info -->
              <div class="flex items-center gap-2 pt-0.5">
                <div class="w-6 h-6 rounded-full bg-[#1b2b4a] border border-sky-400/40 text-sky-300 text-[10px] font-bold flex items-center justify-center shrink-0 shadow-xs">
                  {video.avatarText}
                </div>
                <span class="text-xs text-slate-300 truncate font-medium">
                  {video.channel}
                </span>
                <svg class="w-3 h-3 text-sky-400 shrink-0 fill-current" viewBox="0 0 24 24">
                  <path d="M12 2C6.5 2 2 6.5 2 12s4.5 10 10 10 10-4.5 10-10S17.5 2 12 2zm-1.9 14.7l-4.5-4.5 1.4-1.4 3.1 3.1 7.1-7.1 1.4 1.4-8.5 8.5z" />
                </svg>
              </div>

              <!-- Title -->
              <h2 class="text-base font-bold text-white group-hover:text-sky-300 transition-colors leading-snug line-clamp-2 tracking-tight">
                {video.title}
              </h2>

              <!-- Description -->
              <p class="text-xs text-slate-300 leading-relaxed line-clamp-3 font-normal">
                {video.desc}
              </p>
            </div>

            <!-- Action Button -->
            <div class="pt-4 mt-4 border-t border-sky-500/20">
              <a
                href="https://www.youtube.com/watch?v={video.id}"
                target="_blank"
                rel="noopener noreferrer"
                class="w-full py-2.5 px-4 rounded-xl bg-gradient-to-r from-sky-500 to-blue-600 hover:from-sky-400 hover:to-blue-500 text-white text-xs font-semibold flex items-center justify-center gap-2 transition-all shadow-md shadow-sky-900/50 hover:shadow-sky-900/70 cursor-pointer no-underline"
              >
                <svg class="w-3.5 h-3.5 fill-current text-white transition-colors" viewBox="0 0 24 24">
                  <path d="M8 5v14l11-7z" />
                </svg>
                <span>Tonton di YouTube</span>
                <span class="text-[10px] text-sky-200">↗</span>
              </a>
            </div>
          </article>
        {/each}
      </section>
    {:else}
      <!-- Empty State -->
      <section class="py-16 text-center rounded-3xl bg-[#111c33] border-2 border-sky-500/30 p-8 space-y-3 shadow-xl">
        <div class="text-3xl">🔍</div>
        <h3 class="text-base font-semibold text-white">Tidak ada video yang cocok</h3>
        <p class="text-xs text-slate-400 max-w-sm mx-auto">
          Tidak ditemukan video dengan kata kunci "{searchTerm}". Silakan coba kata kunci lain atau pilih filter kategori.
        </p>
        <button
          type="button"
          onclick={() => {
            searchTerm = "";
            selectedCategory = "all";
          }}
          class="mt-2 px-5 py-2 rounded-full text-xs font-bold bg-gradient-to-r from-sky-500 to-blue-600 text-white hover:from-sky-400 hover:to-blue-500 transition-all shadow-xs cursor-pointer"
        >
          Reset Filter
        </button>
      </section>
    {/if}
  </main>

  <!-- Clean Dark Footer -->
  <footer class="border-t border-slate-800/80 bg-[#050811] py-10">
    <div class="max-w-6xl mx-auto px-6 flex flex-col sm:flex-row items-center justify-between gap-4 text-xs text-slate-400">
      <div class="flex items-center gap-2">
        <span class="text-slate-200 font-bold">IPKD Tube 2026</span>
        <span>•</span>
        <span>Himpunan Video & Panduan Teknis</span>
      </div>
      <div class="text-slate-400 font-medium">
        Rindra Aniko Lab
      </div>
    </div>
  </footer>
</div>