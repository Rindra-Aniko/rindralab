<script lang="ts">
	interface ModuleItem {
		id: string;
		title: string;
		subtitle: string;
		description: string;
		category: 'Dokumen' | 'Video Tutorial';
		status: string;
		statusColor: 'emerald' | 'sky';
		href: string;
		icon: string;
		badge: string;
		stats: { label: string; value: string };
		highlights: { icon: string; name: string; type: string }[];
	}

	let searchQuery = $state('');
	let selectedCategory = $state('Semua');

	const categories = ['Semua', 'Dokumen', 'Video Tutorial'];

	const modules: ModuleItem[] = [
		{
			id: 'riprid',
			title: 'Dokumen RIPRID 2027–2029',
			subtitle: 'Bapperida Kota Sungai Penuh',
			description:
				'Rencana Induk Penelitian Riset & Inovasi Daerah: Rangkaian pemetaan masalah berbasis bukti, analisa kesenjangan, sinkronisasi RPJMD, hingga naskah draf rancangan awal.',
			category: 'Dokumen',
			status: '5 Berkas Terpadu',
			statusColor: 'sky',
			href: '/riprid2026',
			icon: '🏛️',
			badge: 'Perencanaan Strategis',
			stats: { label: 'Tautan Cloud', value: 'Figma • Docs • Sheets' },
			highlights: [
				{ icon: '🎯', name: 'Pemetaan Masalah', type: 'Figma Board' },
				{ icon: '📐', name: 'Analisa Kesenjangan', type: 'Spreadsheet' },
				{ icon: '📊', name: 'Tabel Matriks RPJMD', type: 'Drive Folder' },
				{ icon: '📝', name: 'Draf Ranwal 1 & 2', type: 'Google Docs' }
			]
		},
		{
			id: 'ipkd',
			title: 'Katalog Video IPKD 2026',
			subtitle: 'Bapperida Kota Sungai Penuh',
			description:
				'Pusat multimedia dan panduan teknis penginputan Indeks Pengelolaan Keuangan Daerah (IPKD) Dimensi I hingga VI, simulasi penilaian, dan ketentuan insentif daerah.',
			category: 'Video Tutorial',
			status: '8 Video Tutorial',
			statusColor: 'emerald',
			href: '/ipkd2026',
			icon: '🎬',
			badge: 'Multimedia & Panduan',
			stats: { label: 'Platform', value: 'YouTube Streaming HD' },
			highlights: [
				{ icon: '💡', name: 'IPKD Tolak Ukur APBD', type: 'Informasi' },
				{ icon: '🏆', name: 'Insentif Daerah IPKD', type: 'Insentif Fiskal' },
				{ icon: '⚡', name: 'Tutorial Dimensi I - III', type: 'Teknis Input' },
				{ icon: '📈', name: 'Tutorial Dimensi IV - VI', type: 'Verifikasi Akhir' }
			]
		}
	];

	let filteredModules = $derived(
		modules.filter((item) => {
			const matchCategory = selectedCategory === 'Semua' || item.category === selectedCategory;
			const query = searchQuery.toLowerCase().trim();
			const matchSearch =
				query === '' ||
				item.title.toLowerCase().includes(query) ||
				item.description.toLowerCase().includes(query) ||
				item.subtitle.toLowerCase().includes(query) ||
				item.highlights.some((h) => h.name.toLowerCase().includes(query));
			return matchCategory && matchSearch;
		})
	);
</script>

<svelte:head>
	<title>Rindra Labs • Himpunan Informasi & Eksperimen</title>
	<meta
		name="description"
		content="Rindra Labs - Portal himpunan informasi dan eksperimen digital. Akses dokumen RIPRID 2027-2029 dan panduan video IPKD 2026."
	/>
</svelte:head>

<div class="relative min-h-screen bg-[#f9f7f3] text-[#1d1e22] selection:bg-[#ff8e5e]/30 selection:text-[#1d1e22] font-sans antialiased overflow-x-hidden">
	<!-- Ambient Background Glows (Eleken Warm Canvas subtle accents) -->
	<div class="pointer-events-none absolute inset-0 overflow-hidden">
		<!-- Micro dot grid with warm subtle tone -->
		<div class="absolute inset-0 bg-[radial-gradient(rgba(29,30,34,0.06)_1px,transparent_1px)] [background-size:28px_28px] opacity-70"></div>
		<!-- Top Ambient Warm Glow -->
		<div class="absolute -top-36 left-1/2 -translate-x-1/2 w-[800px] sm:w-[1100px] h-[450px] bg-gradient-to-b from-[#ff8e5e]/10 via-[#ccf095]/10 to-transparent blur-[140px] rounded-full"></div>
		<!-- Ambient Center-Right Accent -->
		<div class="absolute top-[650px] -right-36 w-[550px] h-[550px] bg-[#ff8e5e]/8 blur-[150px] rounded-full"></div>
		<!-- Bottom Left Soft Accent -->
		<div class="absolute top-[1200px] -left-36 w-[600px] h-[600px] bg-[#ccf095]/15 blur-[160px] rounded-full"></div>
	</div>

	<!-- Navigation Bar (Frosted Glass Warm Canvas with Crisp Border) -->
	<header class="sticky top-0 z-50 backdrop-blur-xl bg-[#f9f7f3]/85 border-b border-[#e6e4e0] transition-all duration-300">
		<div class="max-w-6xl mx-auto px-6 h-16 flex items-center justify-between gap-4">
			<a href="/" class="flex items-center gap-3 group">
				<div class="w-8 h-8 rounded-xl bg-[#1d1e22] text-white flex items-center justify-center text-xs font-black shadow-sm group-hover:bg-[#f2723c] group-hover:scale-105 transition-all">
					R
				</div>
				<div class="flex flex-col">
					<span class="text-sm font-bold tracking-tight text-[#1d1e22] group-hover:text-[#f2723c] transition-colors">
						Rindra Labs
					</span>
					<span class="text-[10px] text-[#616264] -mt-0.5 font-medium">
						Eksperimen & Himpunan Informasi
					</span>
				</div>
			</a>

			<div class="flex items-center gap-3">
				<div class="hidden sm:inline-flex items-center gap-2 px-3 py-1 rounded-full bg-[#ccf095]/70 border border-[#b8e578] text-xs text-[#233510]">
					<span class="w-2 h-2 rounded-full bg-[#2d4512] animate-pulse"></span>
					<span class="text-[11px] font-bold">Portal Aktif</span>
				</div>

				<a
					href="#katalog"
					class="text-xs px-4 py-1.5 rounded-full bg-[#f2723c] hover:bg-[#e0622d] text-white font-semibold transition-all shadow-sm hover:shadow-md"
				>
					Jelajahi Modul
				</a>
			</div>
		</div>
	</header>

	<main class="relative max-w-6xl mx-auto px-6 pt-16 pb-28 space-y-24">
		<!-- Hero Section -->
		<section class="text-center max-w-3xl mx-auto space-y-6 pt-4">
			<!-- Pastel Lime Pill Badge with Pulse -->
			<div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full text-xs font-bold bg-[#ccf095] border border-[#b8e578] text-[#1d1e22] shadow-xs">
				<span class="w-2 h-2 rounded-full bg-[#1d1e22] animate-ping"></span>
				<span>LABORATORIUM DIGITAL</span>
				<span class="text-[#616264]">•</span>
				<span class="text-[#2d4512] font-semibold">Rindra Aniko</span>
			</div>

			<!-- Main Grand Heading with Eleken Coral Tint -->
			<h1 class="text-4xl sm:text-6xl md:text-7xl font-extrabold tracking-tight text-[#1d1e22] leading-[1.06]">
				SELAMAT DATANG <br />
				<span class="bg-gradient-to-r from-[#f2723c] via-[#ff8e5e] to-[#f59958] bg-clip-text text-transparent">
					DI LABS.
				</span>
			</h1>

			<!-- Subtitle -->
			<p class="text-lg sm:text-xl text-[#616264] leading-relaxed max-w-2xl mx-auto font-normal">
				"Disini adalah himpunan informasi sekaligus tempat untuk mengeksplorasi berbagai eksperimen"
			</p>

			<!-- Modern Keynote Metric Strip with Eleken Warm Cards -->
			<div class="pt-2 grid grid-cols-3 gap-3.5 max-w-lg mx-auto">
				<div class="p-4 rounded-2xl bg-white border border-[#e6e4e0] hover:border-[#f2723c]/40 hover:shadow-md transition-all text-center shadow-xs">
					<div class="text-2xl sm:text-3xl font-black text-[#f2723c] tracking-tight">{modules.length}</div>
					<div class="text-[11px] text-[#616264] font-bold uppercase tracking-wider mt-0.5">Modul Resmi</div>
				</div>

				<div class="p-4 rounded-2xl bg-white border border-[#e6e4e0] hover:border-[#b8e578] hover:shadow-md transition-all text-center shadow-xs">
					<div class="text-2xl sm:text-3xl font-black text-[#1d1e22] tracking-tight">13+</div>
					<div class="text-[11px] text-[#616264] font-bold uppercase tracking-wider mt-0.5">Berkas & Video</div>
				</div>

				<div class="p-4 rounded-2xl bg-white border border-[#e6e4e0] hover:border-[#f2723c]/40 hover:shadow-md transition-all text-center shadow-xs">
					<div class="text-2xl sm:text-3xl font-black text-[#f2723c] tracking-tight">100%</div>
					<div class="text-[11px] text-[#616264] font-bold uppercase tracking-wider mt-0.5">Akses Cloud</div>
				</div>
			</div>
		</section>

		<!-- Section Showcase: Bento Grid dengan Eleken White Cards on Warm Canvas -->
		<section id="katalog" class="space-y-8 scroll-mt-20">
			<!-- Section Header & Controls -->
			<div class="flex flex-col md:flex-row md:items-end justify-between gap-6 pb-4 border-b border-[#e6e4e0]">
				<div>
					<div class="inline-flex items-center gap-1.5 text-xs uppercase tracking-widest text-[#f2723c] font-bold mb-1">
						<span>✨</span>
						<span>Katalog Modul Unggulan</span>
					</div>
					<h2 class="text-2xl sm:text-3xl font-extrabold tracking-tight text-[#1d1e22]">
						Himpunan & Eksperimen
					</h2>
					<p class="text-sm text-[#616264] mt-1">
						Pilih kartu modul untuk membuka berkas kerja dan tutorial interaktif.
					</p>
				</div>

				<!-- Search & Filter Controls -->
				<div class="flex flex-col sm:flex-row items-stretch sm:items-center gap-3 w-full md:w-auto">
					<!-- Search Box -->
					<div class="relative w-full sm:w-64">
						<svg
							class="w-4 h-4 text-[#8a8b8e] absolute left-3.5 top-1/2 -translate-y-1/2 pointer-events-none"
							fill="none"
							stroke="currentColor"
							viewBox="0 0 24 24"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"
							/>
						</svg>
						<input
							type="text"
							bind:value={searchQuery}
							placeholder="Cari modul, topik, video..."
							class="w-full pl-9 pr-4 py-2 text-xs rounded-full bg-white border border-[#e6e4e0] text-[#1d1e22] placeholder:text-[#8a8b8e] focus:outline-none focus:border-[#f2723c] focus:ring-4 focus:ring-[#f2723c]/15 transition-all shadow-xs"
						/>
					</div>

					<!-- Category Pills (Eleken Pill Style) -->
					<div class="flex items-center gap-1.5 overflow-x-auto pb-1 sm:pb-0">
						{#each categories as category}
							<button
								type="button"
								onclick={() => (selectedCategory = category)}
								class="px-4 py-2 rounded-full text-xs font-bold whitespace-nowrap transition-all cursor-pointer {selectedCategory ===
								category
									? 'bg-[#1d1e22] text-white shadow-xs'
									: 'bg-white text-[#616264] hover:bg-[#f2efe9] hover:text-[#1d1e22] border border-[#e6e4e0]'}"
							>
								{category}
							</button>
						{/each}
					</div>
				</div>
			</div>

			<!-- Bento Grid Cards (Eleken Pure White Cards on Ivory Background) -->
			{#if filteredModules.length > 0}
				<div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
					{#each filteredModules as item}
						<article
							class="group relative rounded-3xl bg-white hover:bg-white border border-[#e6e4e0] hover:border-[#f2723c]/50 p-7 sm:p-8 transition-all duration-300 shadow-[0_4px_24px_rgba(29,30,34,0.04)] hover:shadow-[0_16px_36px_rgba(29,30,34,0.08)] hover:-translate-y-1 flex flex-col justify-between overflow-hidden"
						>
							<!-- Decorative Subtle Accent Line -->
							<div class="pointer-events-none absolute top-0 left-0 right-0 h-1 bg-gradient-to-r from-transparent via-[#f2723c]/60 to-transparent opacity-0 group-hover:opacity-100 transition-opacity"></div>

							<div class="relative z-10 space-y-6">
								<!-- Card Top Row: Icon, Meta Badge & Status -->
								<div class="flex items-center justify-between gap-3">
									<div class="flex items-center gap-3">
										<div class="w-13 h-13 rounded-2xl bg-[#f9f7f3] border border-[#e6e4e0] shadow-xs flex items-center justify-center text-2xl group-hover:scale-105 group-hover:border-[#f2723c]/40 transition-all duration-300">
											{item.icon}
										</div>
										<div>
											<span class="text-[11px] font-bold text-[#f2723c] uppercase tracking-wider block">
												{item.badge}
											</span>
											<span class="text-xs font-semibold text-[#616264]">
												{item.subtitle}
											</span>
										</div>
									</div>

									<span
										class="text-xs font-bold px-3 py-1 rounded-full {item.statusColor === 'emerald'
											? 'bg-[#ccf095] text-[#1d1e22] border border-[#b8e578]'
											: 'bg-[#fff2ec] text-[#f2723c] border border-[#ffcdb5]'}"
									>
										{item.status}
									</span>
								</div>

								<!-- Card Title & Description -->
								<div class="space-y-2 pt-1">
									<h3 class="text-2xl font-bold text-[#1d1e22] group-hover:text-[#f2723c] transition-colors tracking-tight leading-snug">
										<a href={item.href} class="focus:outline-none after:absolute after:inset-0">
											{item.title}
										</a>
									</h3>
									<p class="text-sm text-[#616264] leading-relaxed font-normal">
										{item.description}
									</p>
								</div>

								<!-- Interactive Micro-Previews (Warm Ivory Subcards) -->
								<div class="space-y-2.5 pt-2">
									<span class="text-[11px] font-bold uppercase tracking-wider text-[#1d1e22] block">
										Cakupan Materi & Komponen:
									</span>
									<div class="grid grid-cols-2 gap-2.5">
										{#each item.highlights as hl}
											<div class="p-3 rounded-xl bg-[#f9f7f3] hover:bg-[#f2efe9] border border-[#e6e4e0] flex items-center gap-2.5 shadow-xs transition-colors">
												<span class="text-base shrink-0">{hl.icon}</span>
												<div class="min-w-0">
													<div class="text-xs font-bold text-[#1d1e22] truncate leading-tight group-hover:text-[#f2723c]">
														{hl.name}
													</div>
													<div class="text-[10px] font-medium text-[#616264] truncate">
														{hl.type}
													</div>
												</div>
											</div>
										{/each}
									</div>
								</div>
							</div>

							<!-- Card Footer / Bottom Bar -->
							<div class="relative z-10 pt-6 mt-6 border-t border-[#e6e4e0] flex items-center justify-between gap-4">
								<div class="text-xs text-[#616264] font-medium truncate">
									<span>Integrasi: </span>
									<strong class="text-[#1d1e22]">{item.stats.value}</strong>
								</div>

								<!-- Action Button (Eleken Coral Pill) -->
								<a
									href={item.href}
									class="relative z-20 inline-flex items-center gap-2 px-5 py-2.5 rounded-full bg-[#f2723c] hover:bg-[#e0622d] text-white text-xs font-bold transition-all shadow-sm hover:shadow-md hover:scale-[1.03] active:scale-[0.98] shrink-0 cursor-pointer no-underline"
								>
									<span>Buka Halaman</span>
									<svg
										class="w-3.5 h-3.5 transform group-hover:translate-x-1 transition-transform"
										fill="none"
										stroke="currentColor"
										viewBox="0 0 24 24"
									>
										<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M9 5l7 7-7 7" />
									</svg>
								</a>
							</div>
						</article>
					{/each}
				</div>
			{:else}
				<!-- Empty State -->
				<div class="py-20 text-center rounded-3xl bg-white border border-[#e6e4e0] p-8 space-y-3 shadow-xs">
					<div class="text-4xl">🔍</div>
					<h3 class="text-lg font-bold text-[#1d1e22]">Tidak ada modul yang cocok</h3>
					<p class="text-xs sm:text-sm text-[#616264] max-w-sm mx-auto">
						Tidak ditemukan hasil pencarian dengan kata kunci "{searchQuery}". Silakan coba kata kunci lain.
					</p>
					<button
						type="button"
						onclick={() => {
							searchQuery = '';
							selectedCategory = 'Semua';
						}}
						class="mt-3 px-5 py-2 rounded-full text-xs font-bold bg-[#1d1e22] text-white hover:bg-[#2d2e33] transition-all shadow-xs cursor-pointer"
					>
						Reset Pencarian
					</button>
				</div>
			{/if}
		</section>

		<!-- Feature Highlight / Philosophy Banner (Eleken Charcoal Statement Card) -->
		<section class="relative rounded-3xl bg-[#1d1e22] text-white border border-[#2d2e33] p-8 sm:p-12 text-center space-y-5 shadow-xl overflow-hidden">
			<!-- Subtle ambient warmth inside dark section -->
			<div class="pointer-events-none absolute -top-24 -right-24 w-80 h-80 bg-[#f2723c]/20 rounded-full blur-3xl"></div>
			<div class="pointer-events-none absolute -bottom-24 -left-24 w-80 h-80 bg-[#ccf095]/15 rounded-full blur-3xl"></div>

			<div class="relative z-10 inline-flex items-center gap-2 px-3.5 py-1 rounded-full text-[11px] font-bold bg-[#ccf095] text-[#1d1e22] shadow-xs">
				<span>🏛️</span>
				<span>SISTEM INFORMASI TERBUKA</span>
			</div>

			<h2 class="relative z-10 text-2xl sm:text-4xl font-extrabold text-white tracking-tight">
				Membangun Perencanaan Berbasis Data & Riset.
			</h2>

			<p class="relative z-10 text-sm sm:text-base text-[#a0a1a5] max-w-2xl mx-auto leading-relaxed font-normal">
				Setiap berkas dan dokumentasi eksperimen disusun secara sistematis agar dapat diakses oleh publik, akademisi, dan perangkat daerah guna mendorong inovasi Kota Sungai Penuh.
			</p>

			<div class="relative z-10 pt-3 flex flex-wrap items-center justify-center gap-3">
				<a
					href="/riprid2026"
					class="px-5 py-2.5 rounded-full bg-[#f2723c] hover:bg-[#e0622d] text-white text-xs font-bold transition-all shadow-sm hover:scale-[1.02]"
				>
					Akses RIPRID 2027–2029 →
				</a>
				<a
					href="/ipkd2026"
					class="px-5 py-2.5 rounded-full bg-white/10 hover:bg-white/20 text-white text-xs font-bold transition-all border border-white/20 shadow-sm"
				>
					Tonton IPKD Tube 2026 →
				</a>
			</div>
		</section>
	</main>

	<!-- Footer with Clean Eleken Line -->
	<footer class="border-t border-[#e6e4e0] bg-[#f2efe9] py-12">
		<div class="max-w-6xl mx-auto px-6 flex flex-col sm:flex-row items-center justify-between gap-6 text-xs text-[#616264]">
			<div class="flex items-center gap-3">
				<div class="w-6 h-6 rounded-lg bg-[#1d1e22] text-white flex items-center justify-center text-[10px] font-bold shadow-xs">
					R
				</div>
				<span class="text-[#1d1e22] font-bold">uji coba rindra aniko</span>
				<span>•</span>
				<span>Eksperimen & Himpunan Berkas</span>
			</div>

			<div class="flex items-center gap-4 text-[#616264] font-medium">
				<a href="/riprid2026" class="hover:text-[#f2723c] transition-colors">RIPRID 2026</a>
				<span>•</span>
				<a href="/ipkd2026" class="hover:text-[#f2723c] transition-colors">IPKD 2026</a>
				<span>•</span>
				<span>Kota Sungai Penuh</span>
			</div>
		</div>
	</footer>
</div>
