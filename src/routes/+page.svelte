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

<div class="relative min-h-screen bg-[#070b14] text-slate-100 selection:bg-sky-500/30 selection:text-sky-200 font-sans antialiased overflow-x-hidden">
	<!-- Ambient Background Glows (Deep Dark Blue / Midnight Obsidian Glows) -->
	<div class="pointer-events-none absolute inset-0 overflow-hidden">
		<!-- Micro dot grid with subtle dark sky hint -->
		<div class="absolute inset-0 bg-[radial-gradient(rgba(56,189,248,0.12)_1px,transparent_1px)] [background-size:24px_24px] opacity-35"></div>
		<!-- Top Ambient Deep Blue Glow -->
		<div class="absolute -top-36 left-1/2 -translate-x-1/2 w-[800px] sm:w-[1100px] h-[450px] bg-gradient-to-b from-sky-600/15 via-blue-700/10 to-transparent blur-[140px] rounded-full"></div>
		<!-- Ambient Center-Right Accent -->
		<div class="absolute top-[650px] -right-36 w-[550px] h-[550px] bg-blue-900/15 blur-[150px] rounded-full"></div>
		<!-- Bottom Left Soft Accent -->
		<div class="absolute top-[1200px] -left-36 w-[600px] h-[600px] bg-sky-900/15 blur-[160px] rounded-full"></div>
	</div>

	<!-- Navigation Bar (Dark Frosted Glass with Deep Blue Border) -->
	<header class="sticky top-0 z-50 backdrop-blur-xl bg-[#070b14]/85 border-b border-slate-800/80 transition-all duration-300">
		<div class="max-w-6xl mx-auto px-6 h-16 flex items-center justify-between gap-4">
			<a href="/" class="flex items-center gap-3 group">
				<div class="w-8 h-8 rounded-xl bg-gradient-to-br from-sky-500 to-blue-600 text-white flex items-center justify-center text-xs font-black shadow-md shadow-sky-500/25 group-hover:scale-105 transition-transform">
					R
				</div>
				<div class="flex flex-col">
					<span class="text-sm font-bold tracking-tight text-white group-hover:text-sky-400 transition-colors">
						Rindra Labs
					</span>
					<span class="text-[10px] text-sky-400/80 -mt-0.5 font-medium">
						Eksperimen & Himpunan Informasi
					</span>
				</div>
			</a>

			<div class="flex items-center gap-3">
				<div class="hidden sm:inline-flex items-center gap-2 px-3 py-1 rounded-full bg-sky-950/60 border border-sky-800/60 text-xs text-sky-300">
					<span class="w-2 h-2 rounded-full bg-sky-400 animate-pulse"></span>
					<span class="text-[11px] font-semibold">Portal Aktif</span>
				</div>

				<a
					href="#katalog"
					class="text-xs px-4 py-1.5 rounded-full bg-gradient-to-r from-sky-500 to-blue-600 hover:from-sky-400 hover:to-blue-500 text-white font-semibold transition-all shadow-md shadow-sky-900/40"
				>
					Jelajahi Modul
				</a>
			</div>
		</div>
	</header>

	<main class="relative max-w-6xl mx-auto px-6 pt-16 pb-28 space-y-24">
		<!-- Hero Section -->
		<section class="text-center max-w-3xl mx-auto space-y-6 pt-4">
			<!-- Soft Blue Pill Badge with Pulse -->
			<div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full text-xs font-semibold bg-sky-950/60 border border-sky-800/60 text-sky-300 shadow-2xs">
				<span class="w-2 h-2 rounded-full bg-sky-400 animate-ping"></span>
				<span class="text-sky-300">LABORATORIUM DIGITAL</span>
				<span class="text-sky-700">•</span>
				<span class="text-sky-400/90 font-medium">Rindra Aniko</span>
			</div>

			<!-- Main Grand Heading with Subtle Tint -->
			<h1 class="text-4xl sm:text-6xl md:text-7xl font-extrabold tracking-tight text-white leading-[1.06]">
				SELAMAT DATANG <br />
				<span class="bg-gradient-to-r from-sky-400 via-blue-400 to-indigo-400 bg-clip-text text-transparent">
					DI LABS.
				</span>
			</h1>

			<!-- Subtitle -->
			<p class="text-lg sm:text-xl text-slate-300 leading-relaxed max-w-2xl mx-auto font-normal">
				"Disini adalah himpunan informasi sekaligus tempat untuk mengeksplorasi berbagai eksperimen"
			</p>

			<!-- Modern Keynote Metric Strip with Dark Blue Tints -->
			<div class="pt-2 grid grid-cols-3 gap-3.5 max-w-lg mx-auto">
				<div class="p-4 rounded-2xl bg-[#111c33] border border-sky-500/25 hover:border-sky-400/50 transition-all text-center shadow-lg shadow-black/40">
					<div class="text-2xl sm:text-3xl font-black text-sky-300 tracking-tight">{modules.length}</div>
					<div class="text-[11px] text-sky-400/80 font-semibold uppercase tracking-wider mt-0.5">Modul Resmi</div>
				</div>

				<div class="p-4 rounded-2xl bg-[#111c33] border border-sky-500/25 hover:border-sky-400/50 transition-all text-center shadow-lg shadow-black/40">
					<div class="text-2xl sm:text-3xl font-black text-emerald-400 tracking-tight">13+</div>
					<div class="text-[11px] text-slate-300 font-semibold uppercase tracking-wider mt-0.5">Berkas & Video</div>
				</div>

				<div class="p-4 rounded-2xl bg-[#111c33] border border-sky-500/25 hover:border-sky-400/50 transition-all text-center shadow-lg shadow-black/40">
					<div class="text-2xl sm:text-3xl font-black text-sky-400 tracking-tight">100%</div>
					<div class="text-[11px] text-sky-400/80 font-semibold uppercase tracking-wider mt-0.5">Akses Cloud</div>
				</div>
			</div>
		</section>

		<!-- Section Showcase: Bento Grid dengan Dark Blue / Midnight Black Theme -->
		<section id="katalog" class="space-y-8 scroll-mt-20">
			<!-- Section Header & Controls -->
			<div class="flex flex-col md:flex-row md:items-end justify-between gap-6 pb-4 border-b border-slate-800/80">
				<div>
					<div class="inline-flex items-center gap-1.5 text-xs uppercase tracking-widest text-sky-400 font-bold mb-1">
						<span>✨</span>
						<span>Katalog Modul Unggulan</span>
					</div>
					<h2 class="text-2xl sm:text-3xl font-extrabold tracking-tight text-white">
						Himpunan & Eksperimen
					</h2>
					<p class="text-sm text-slate-400 mt-1">
						Pilih kartu modul untuk membuka berkas kerja dan tutorial interaktif.
					</p>
				</div>

				<!-- Search & Filter Controls -->
				<div class="flex flex-col sm:flex-row items-stretch sm:items-center gap-3 w-full md:w-auto">
					<!-- Search Box (Dark Navy Tint) -->
					<div class="relative w-full sm:w-64">
						<svg
							class="w-4 h-4 text-sky-400 absolute left-3.5 top-1/2 -translate-y-1/2 pointer-events-none"
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
							class="w-full pl-9 pr-4 py-2 text-xs rounded-full bg-[#111c33] border border-sky-500/30 text-slate-100 placeholder:text-slate-400 focus:outline-none focus:bg-[#15233e] focus:border-sky-400 focus:ring-4 focus:ring-sky-500/25 transition-all shadow-inner"
						/>
					</div>

					<!-- Category Pills (Blue Highlight) -->
					<div class="flex items-center gap-1.5 overflow-x-auto pb-1 sm:pb-0">
						{#each categories as category}
							<button
								type="button"
								onclick={() => (selectedCategory = category)}
								class="px-4 py-2 rounded-full text-xs font-semibold whitespace-nowrap transition-all cursor-pointer {selectedCategory ===
								category
									? 'bg-gradient-to-r from-sky-500 to-blue-600 text-white shadow-sm shadow-sky-600/30'
									: 'bg-[#111c33] text-slate-300 hover:bg-[#162544] hover:text-white border border-sky-500/20'}"
							>
								{category}
							</button>
						{/each}
					</div>
				</div>
			</div>

			<!-- Bento Grid Cards (Kombinasi Biru Gelap Kontras & Menonjol) -->
			{#if filteredModules.length > 0}
				<div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
					{#each filteredModules as item}
						<article
							class="group relative rounded-3xl bg-gradient-to-b from-[#142038] via-[#101a2f] to-[#0c1527] hover:from-[#192847] hover:via-[#132039] hover:to-[#0f1a30] border-2 border-sky-500/30 hover:border-sky-400/70 p-7 sm:p-8 transition-all duration-300 shadow-xl shadow-black/60 hover:shadow-2xl hover:shadow-sky-900/40 hover:-translate-y-1.5 flex flex-col justify-between overflow-hidden ring-1 ring-white/5"
						>
							<!-- Decorative Ambient Glow Inside Card -->
							<div
								class="pointer-events-none absolute -top-24 -right-24 w-64 h-64 bg-gradient-to-br from-sky-500/20 via-blue-600/15 to-transparent rounded-full blur-3xl group-hover:scale-125 transition-transform duration-500 opacity-90"
							></div>

							<!-- Subtle Top Border Highlight Line -->
							<div class="pointer-events-none absolute top-0 left-0 right-0 h-1 bg-gradient-to-r from-transparent via-sky-400/70 to-transparent opacity-60 group-hover:opacity-100 transition-opacity"></div>

							<div class="relative z-10 space-y-6">
								<!-- Card Top Row: Icon, Meta Badge & Status -->
								<div class="flex items-center justify-between gap-3">
									<div class="flex items-center gap-3">
										<div class="w-13 h-13 rounded-2xl bg-[#1b2b4a] border border-sky-400/40 shadow-md shadow-sky-950/40 flex items-center justify-center text-2xl group-hover:scale-105 group-hover:border-sky-300 transition-all duration-300">
											{item.icon}
										</div>
										<div>
											<span class="text-[11px] font-bold text-sky-400 uppercase tracking-wider block">
												{item.badge}
											</span>
											<span class="text-xs font-semibold text-slate-300">
												{item.subtitle}
											</span>
										</div>
									</div>

									<span
										class="text-xs font-bold px-3 py-1 rounded-full {item.statusColor === 'emerald'
											? 'bg-emerald-950/90 text-emerald-300 border border-emerald-700/80 shadow-xs'
											: 'bg-sky-950/90 text-sky-300 border border-sky-700/80 shadow-xs'}"
									>
										{item.status}
									</span>
								</div>

								<!-- Card Title & Description -->
								<div class="space-y-2 pt-1">
									<h3 class="text-2xl font-bold text-white group-hover:text-sky-300 transition-colors tracking-tight leading-snug">
										<a href={item.href} class="focus:outline-none after:absolute after:inset-0">
											{item.title}
										</a>
									</h3>
									<p class="text-sm text-slate-300 leading-relaxed font-normal">
										{item.description}
									</p>
								</div>

								<!-- Interactive Micro-Previews (Dark Sky Blue Boxes) -->
								<div class="space-y-2.5 pt-2">
									<span class="text-[11px] font-bold uppercase tracking-wider text-sky-400 block">
										Cakupan Materi & Komponen:
									</span>
									<div class="grid grid-cols-2 gap-2.5">
										{#each item.highlights as hl}
											<div class="p-3 rounded-xl bg-[#0a1120]/90 hover:bg-[#121e35] border border-sky-500/20 hover:border-sky-400/40 flex items-center gap-2.5 shadow-sm transition-colors">
												<span class="text-base shrink-0">{hl.icon}</span>
												<div class="min-w-0">
													<div class="text-xs font-bold text-slate-100 truncate leading-tight group-hover:text-sky-200">
														{hl.name}
													</div>
													<div class="text-[10px] font-medium text-sky-400 truncate">
														{hl.type}
													</div>
												</div>
											</div>
										{/each}
									</div>
								</div>
							</div>

							<!-- Card Footer / Bottom Bar -->
							<div class="relative z-10 pt-6 mt-6 border-t border-sky-500/20 flex items-center justify-between gap-4">
								<div class="text-xs text-slate-300 font-medium truncate">
									<span>Integrasi: </span>
									<strong class="text-sky-300">{item.stats.value}</strong>
								</div>

								<!-- Action Button -->
								<a
									href={item.href}
									class="relative z-20 inline-flex items-center gap-2 px-5 py-2.5 rounded-full bg-gradient-to-r from-sky-500 to-blue-600 hover:from-sky-400 hover:to-blue-500 text-white text-xs font-bold transition-all shadow-md shadow-sky-900/50 hover:shadow-lg hover:shadow-sky-900/70 hover:scale-[1.03] active:scale-[0.98] shrink-0 cursor-pointer no-underline"
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
				<div class="py-20 text-center rounded-3xl bg-[#111c33] border-2 border-sky-500/30 p-8 space-y-3 shadow-xl">
					<div class="text-4xl">🔍</div>
					<h3 class="text-lg font-bold text-white">Tidak ada modul yang cocok</h3>
					<p class="text-xs sm:text-sm text-slate-400 max-w-sm mx-auto">
						Tidak ditemukan hasil pencarian dengan kata kunci "{searchQuery}". Silakan coba kata kunci lain.
					</p>
					<button
						type="button"
						onclick={() => {
							searchQuery = '';
							selectedCategory = 'Semua';
						}}
						class="mt-3 px-5 py-2 rounded-full text-xs font-bold bg-gradient-to-r from-sky-500 to-blue-600 text-white hover:from-sky-400 hover:to-blue-500 transition-all shadow-xs cursor-pointer"
					>
						Reset Pencarian
					</button>
				</div>
			{/if}
		</section>

		<!-- Feature Highlight / Philosophy Banner (Dark Mode Aesthetic) -->
		<section class="relative rounded-3xl bg-gradient-to-b from-[#142038] via-[#101a2f] to-[#0c1527] border-2 border-sky-500/30 p-8 sm:p-12 text-center space-y-4 shadow-xl shadow-black/60 overflow-hidden ring-1 ring-white/5">
			<!-- Subtle Top Light Line -->
			<div class="pointer-events-none absolute top-0 left-0 right-0 h-1 bg-gradient-to-r from-transparent via-sky-400/60 to-transparent"></div>

			<div class="inline-flex items-center gap-2 px-3.5 py-1 rounded-full text-[11px] font-bold bg-[#1b2b4a] text-sky-300 border border-sky-400/40 shadow-xs">
				<span>🏛️</span>
				<span>Sistem Informasi Terbuka</span>
			</div>

			<h2 class="text-2xl sm:text-4xl font-extrabold text-white tracking-tight">
				Membangun Perencanaan Berbasis Data & Riset.
			</h2>

			<p class="text-sm sm:text-base text-slate-300 max-w-2xl mx-auto leading-relaxed font-normal">
				Setiap berkas dan dokumentasi eksperimen disusun secara sistematis agar dapat diakses oleh publik, akademisi, dan perangkat daerah guna mendorong inovasi Kota Sungai Penuh.
			</p>

			<div class="pt-4 flex flex-wrap items-center justify-center gap-3">
				<a
					href="/riprid2026"
					class="px-5 py-2.5 rounded-full bg-[#1b2b4a] hover:bg-sky-600 text-slate-100 hover:text-white text-xs font-bold transition-all border border-sky-400/40 hover:border-sky-300 shadow-md"
				>
					Akses RIPRID 2027–2029 →
				</a>
				<a
					href="/ipkd2026"
					class="px-5 py-2.5 rounded-full bg-[#1b2b4a] hover:bg-sky-600 text-slate-100 hover:text-white text-xs font-bold transition-all border border-sky-400/40 hover:border-sky-300 shadow-md"
				>
					Tonton IPKD Tube 2026 →
				</a>
			</div>
		</section>
	</main>

	<!-- Footer with Clean Dark Slate Line -->
	<footer class="border-t border-slate-800/80 bg-[#050811] py-12">
		<div class="max-w-6xl mx-auto px-6 flex flex-col sm:flex-row items-center justify-between gap-6 text-xs text-slate-400">
			<div class="flex items-center gap-3">
				<div class="w-6 h-6 rounded-lg bg-gradient-to-br from-sky-500 to-blue-600 text-white flex items-center justify-center text-[10px] font-bold shadow-xs">
					R
				</div>
				<span class="text-slate-200 font-bold">uji coba rindra aniko</span>
				<span>•</span>
				<span>Eksperimen & Himpunan Berkas</span>
			</div>

			<div class="flex items-center gap-4 text-slate-400 font-medium">
				<a href="/riprid2026" class="hover:text-sky-400 transition-colors">RIPRID 2026</a>
				<span>•</span>
				<a href="/ipkd2026" class="hover:text-sky-400 transition-colors">IPKD 2026</a>
				<span>•</span>
				<span>Kota Sungai Penuh</span>
			</div>
		</div>
	</footer>
</div>
