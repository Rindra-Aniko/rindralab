<script lang="ts">
	interface DocumentCard {
		id: string;
		step: string;
		stepNumber: string;
		title: string;
		subtitle: string;
		description: string;
		platform: string;
		platformIcon: string;
		platformColor: string;
		href: string;
		icon: string;
		status: 'Tersedia' | 'Draf Kerja' | 'Final';
		highlights: string[];
		ctaLabel: string;
	}

	const mainDocuments: DocumentCard[] = [
		{
			id: 'masalah',
			step: 'Tahap 01',
			stepNumber: '01',
			title: 'Pemetaan Masalah',
			subtitle: 'Identifikasi Akar Isu & Prioritas Daerah',
			description:
				'Papan kerja visual interaktif untuk membedah akar permasalahan pembangunan, klaster isu strategis, dan potensi riset Kota Sungai Penuh.',
			platform: 'Figma Board',
			platformIcon: '🎨',
			platformColor: 'bg-purple-950/70 text-purple-300 border-purple-800/60',
			href: 'https://www.figma.com/board/IUgUSXyF2nzay0SFQo6AQm/RIPRID?node-id=0-1&p=f',
			icon: '🎯',
			status: 'Tersedia',
			highlights: ['Isu Strategis Daerah', 'Analisis Pohon Masalah', 'Prioritas Riset Daerah'],
			ctaLabel: 'Buka Figma Board'
		},
		{
			id: 'kesenjangan',
			step: 'Tahap 02',
			stepNumber: '02',
			title: 'Analisa Kesenjangan',
			subtitle: 'Matriks Gap Eksisting vs Target Indikator',
			description:
				'Spreadsheet kalkulasi komparasi antara kondisi capaian riset saat ini dengan target indikator kinerja riset dan inovasi yang diharapkan.',
			platform: 'Google Sheets',
			platformIcon: '📊',
			platformColor: 'bg-emerald-950/70 text-emerald-300 border-emerald-800/60',
			href: 'https://docs.google.com/spreadsheets/d/1pCIGHyh6ZzSjCnshVe8fjmwtJwoc2eica4Jm-K5MKPE/edit?gid=0#gid=0',
			icon: '📐',
			status: 'Tersedia',
			highlights: ['Kondisi Eksisting', 'Target Capaian RIPRID', 'Matriks Gap Kinerja'],
			ctaLabel: 'Buka Spreadsheet'
		},
		{
			id: 'rpjmd',
			step: 'Tahap 03',
			stepNumber: '03',
			title: 'Tabel Pemetaan RPJMD',
			subtitle: 'Sinkronisasi Visi, Misi & Matriks RPJMD',
			description:
				'Kumpulan berkas sinkronisasi program perangkat daerah dengan sasaran makro RPJMD Kota Sungai Penuh agar riset terintegrasi penuh.',
			platform: 'Google Drive Folder',
			platformIcon: '📁',
			platformColor: 'bg-amber-950/70 text-amber-300 border-amber-800/60',
			href: 'https://drive.google.com/drive/folders/1o0oLV773TZlqT-t65G84F510y7dfJ4AR',
			icon: '📊',
			status: 'Tersedia',
			highlights: ['Penyelarasan RPJMD', 'Matriks Program SKPD', 'Peta Jalan Kebijakan'],
			ctaLabel: 'Akses Folder Drive'
		}
	];

	const draftDocuments: DocumentCard[] = [
		{
			id: 'draf-1',
			step: 'Tahap 04',
			stepNumber: '04',
			title: 'Draf 1 Ranwal',
			subtitle: 'Rancangan Awal Dokumen RIPRID (v1.0)',
			description:
				'Naskah formulasi awal penyusunan Rencana Induk Riset dan Inovasi Daerah hasil kompilasi kajian latar belakang, arah kebijakan, dan peta jalan riset.',
			platform: 'Google Docs',
			platformIcon: '📝',
			platformColor: 'bg-sky-950/70 text-sky-300 border-sky-800/60',
			href: 'https://docs.google.com/document/d/1ekmUrH1bLjS-zVLHQiPr88VeeXvvvqRE/edit?rtpof=true&sd=true&tab=t.0',
			icon: '📝',
			status: 'Draf Kerja',
			highlights: ['Kompilasi Bab I–VI', 'Rumusan Ranwal Awal', 'Kerangka Kebijakan'],
			ctaLabel: 'Buka Naskah Draf 1'
		},
		{
			id: 'draf-2',
			step: 'Tahap 05',
			stepNumber: '05',
			title: 'Draf 2 Ranwal',
			subtitle: 'Naskah Penyempurnaan Hasil Evaluasi',
			description:
				'Naskah finalisasi rancangan awal yang telah mengadopsi masukan para pemangku kepentingan, telaah akademis, dan konsultasi perangkat daerah.',
			platform: 'Google Docs',
			platformIcon: '✨',
			platformColor: 'bg-blue-950/70 text-blue-300 border-blue-800/60',
			href: 'https://docs.google.com/document/d/1bKg7X7zFS-IgS4UT1Xx5p23g2o9da5jJKY7mN-v-CDA/edit?tab=t.0',
			icon: '✨',
			status: 'Final',
			highlights: ['Masukan Konsultasi Publik', 'Penyempurnaan Indikator', 'Naskah Matang Ranwal'],
			ctaLabel: 'Buka Naskah Draf 2'
		}
	];

	const referensiLink =
		'https://drive.google.com/drive/folders/1yYL8GyNCqk4tSeQu_fGtzhvZC3x6QN7H';
	const waLink =
		'https://api.whatsapp.com/send/?phone=%2B6285381822888&text&type=phone_number&app_absent=0';
</script>

<svelte:head>
	<title>RIPRID 2027–2029 • Bapperida Kota Sungai Penuh | Dokumen Perencanaan</title>
	<meta
		name="description"
		content="Pusat Dokumen Resmi RIPRID 2027-2029 Bapperida Kota Sungai Penuh: Pemetaan Masalah, Analisa Kesenjangan, Sinkronisasi RPJMD, Draf Ranwal 1 & 2."
	/>
</svelte:head>

<div class="relative min-h-screen bg-[#070b14] text-slate-100 selection:bg-sky-500/30 selection:text-sky-200 font-sans antialiased overflow-x-hidden">
	<!-- Ambient Background Glows (Deep Dark Blue / Midnight Obsidian Glows) -->
	<div class="pointer-events-none absolute inset-0 overflow-hidden">
		<!-- Micro subtle dot grid -->
		<div class="absolute inset-0 bg-[radial-gradient(rgba(56,189,248,0.12)_1px,transparent_1px)] [background-size:24px_24px] opacity-35"></div>
		<!-- Top Center Deep Blue Ambient Light -->
		<div class="absolute -top-40 left-1/2 -translate-x-1/2 w-[900px] sm:w-[1200px] h-[520px] bg-gradient-to-b from-sky-600/15 via-blue-700/10 to-transparent blur-[140px] rounded-full"></div>
		<!-- Mid Ambient Accent -->
		<div class="absolute top-[800px] -right-40 w-[600px] h-[600px] bg-blue-900/15 blur-[150px] rounded-full"></div>
		<!-- Bottom Accent -->
		<div class="absolute top-[1500px] -left-40 w-[550px] h-[550px] bg-sky-900/15 blur-[160px] rounded-full"></div>
	</div>

	<!-- Navigation Bar (Dark Frosted Glass with Deep Blue Border) -->
	<header class="sticky top-0 z-40 backdrop-blur-xl bg-[#070b14]/85 border-b border-slate-800/80 transition-all duration-300">
		<div class="max-w-6xl mx-auto px-6 h-16 flex items-center justify-between gap-4">
			<div class="flex items-center gap-3">
				<a
					href="/"
					class="inline-flex items-center gap-1.5 px-3.5 py-1.5 rounded-full text-xs font-semibold text-slate-300 hover:text-white bg-slate-900/80 hover:bg-slate-800 border border-slate-700/80 transition-all shadow-xs group"
				>
					<svg class="w-3.5 h-3.5 group-hover:-translate-x-0.5 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M15 19l-7-7 7-7" />
					</svg>
					<span>Beranda</span>
				</a>
				<span class="text-slate-700">/</span>
				<div class="flex items-center gap-2">
					<div class="w-7 h-7 rounded-lg bg-gradient-to-br from-sky-500 to-blue-600 text-white flex items-center justify-center text-xs font-black shadow-xs">
						R
					</div>
					<span class="text-sm font-bold tracking-tight text-white">
						RIPRID
					</span>
					<span class="text-[11px] font-semibold px-2.5 py-0.5 rounded-full bg-sky-950/80 border border-sky-800/80 text-sky-300">
						2027–2029
					</span>
				</div>
			</div>

			<div class="flex items-center gap-2.5">
				<a
					href={waLink}
					target="_blank"
					rel="noopener noreferrer"
					class="inline-flex items-center gap-1.5 px-3.5 py-1.5 rounded-full text-xs font-semibold bg-emerald-950/80 text-emerald-300 border border-emerald-800/80 hover:bg-emerald-900/80 transition-colors shadow-xs"
				>
					<span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span>
					<span class="hidden sm:inline">Konsultasi</span> WhatsApp
				</a>
			</div>
		</div>
	</header>

	<main class="relative max-w-6xl mx-auto px-6 pt-14 pb-28 space-y-20">
		<!-- HERO SECTION DI ATAS (CENTERED & MODERN DARK BLUE STYLE) -->
		<section class="text-center max-w-4xl mx-auto space-y-6 pt-2">
			<!-- Pill Badge -->
			<div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full text-xs font-semibold bg-sky-950/60 border border-sky-800/70 text-sky-300 shadow-2xs">
				<span class="w-2 h-2 rounded-full bg-sky-400 animate-pulse"></span>
				<span class="font-bold tracking-wide text-sky-300">BAPPERIDA KOTA SUNGAI PENUH</span>
				<span class="text-sky-700">•</span>
				<span class="font-medium text-sky-400/90">PERENCANAAN STRATEGIS RISET</span>
			</div>

			<!-- Main Headline -->
			<div class="space-y-3">
				<h1 class="text-3xl sm:text-5xl md:text-6xl font-extrabold tracking-tight text-white leading-[1.12]">
					Rencana Induk Penelitian, Riset <br class="hidden sm:inline" />
					<span class="bg-gradient-to-r from-sky-400 via-blue-400 to-indigo-400 bg-clip-text text-transparent">
						& Inovasi Daerah (RIPRID)
					</span>
				</h1>
				<p class="text-xs sm:text-sm font-bold tracking-widest uppercase text-sky-400/80">
					KOTA SUNGAI PENUH • PERIODE 2027–2029
				</p>
			</div>

			<!-- Subtitle / Narrative -->
			<p class="text-base sm:text-lg text-slate-300 max-w-2xl mx-auto leading-relaxed font-normal">
				Dokumen panduan strategis ekosistem riset, sains, dan inovasi daerah guna mewujudkan kebijakan pembangunan berbasis bukti ilmiah (<em>evidence-based policy</em>) yang selaras dengan dokumen RPJMD.
			</p>

			<!-- Quick Metric & Status Chips (Dark Mode Style) -->
			<div class="pt-3 grid grid-cols-2 sm:grid-cols-4 gap-3 max-w-2xl mx-auto">
				<div class="p-3.5 rounded-2xl bg-[#111c33] border border-sky-500/25 hover:border-sky-400/50 transition-all text-center shadow-lg shadow-black/40">
					<div class="text-xl sm:text-2xl font-black text-sky-300">5 Tahap</div>
					<div class="text-[10px] text-sky-400/80 font-bold uppercase tracking-wider mt-0.5">Dokumen Kerja</div>
				</div>
				<div class="p-3.5 rounded-2xl bg-[#111c33] border border-sky-500/25 hover:border-sky-400/50 transition-all text-center shadow-lg shadow-black/40">
					<div class="text-xl sm:text-2xl font-black text-emerald-400">RPJMD</div>
					<div class="text-[10px] text-slate-300 font-bold uppercase tracking-wider mt-0.5">Sinkronisasi</div>
				</div>
				<div class="p-3.5 rounded-2xl bg-[#111c33] border border-sky-500/25 hover:border-sky-400/50 transition-all text-center shadow-lg shadow-black/40">
					<div class="text-xl sm:text-2xl font-black text-sky-400">100%</div>
					<div class="text-[10px] text-sky-400/80 font-bold uppercase tracking-wider mt-0.5">Cloud Terpadu</div>
				</div>
				<div class="p-3.5 rounded-2xl bg-[#111c33] border border-sky-500/25 hover:border-sky-400/50 transition-all text-center shadow-lg shadow-black/40">
					<div class="text-xl sm:text-2xl font-black text-blue-400">Draf 2</div>
					<div class="text-[10px] text-slate-300 font-bold uppercase tracking-wider mt-0.5">Status Ranwal</div>
				</div>
			</div>

			<!-- Quick Action Buttons -->
			<div class="pt-2 flex flex-wrap items-center justify-center gap-3">
				<a
					href="#tahapan-kerja"
					class="px-5 py-2.5 rounded-full bg-gradient-to-r from-sky-500 to-blue-600 hover:from-sky-400 hover:to-blue-500 text-white text-xs font-bold shadow-md shadow-sky-900/50 hover:shadow-lg hover:shadow-sky-900/70 hover:scale-105 active:scale-95 transition-all inline-flex items-center gap-2 cursor-pointer no-underline"
				>
					<span>Lihat Berkas & Dokumen</span>
					<svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M19 9l-7 7-7-7" />
					</svg>
				</a>
				<a
					href={referensiLink}
					target="_blank"
					rel="noopener noreferrer"
					class="px-5 py-2.5 rounded-full bg-[#111c33] hover:bg-[#162544] text-slate-200 text-xs font-bold border border-sky-500/30 transition-all inline-flex items-center gap-1.5 shadow-sm"
				>
					<span>📚 Pustaka Regulasi</span>
					<span class="text-[10px] text-sky-400">↗</span>
				</a>
			</div>
		</section>

		<!-- SECTION: TAHAPAN UTAMA PENYUSUNAN (CARD BENTO DI BAWAH HERO) -->
		<section id="tahapan-kerja" class="space-y-10 scroll-mt-24">
			<!-- Section Header -->
			<div class="flex flex-col sm:flex-row sm:items-end justify-between gap-4 pb-4 border-b border-slate-800/80">
				<div>
					<div class="inline-flex items-center gap-2 text-xs font-bold uppercase tracking-widest text-sky-400 mb-1">
						<span>📑</span>
						<span>Alur Perumusan Dokumen</span>
					</div>
					<h2 class="text-2xl sm:text-3xl font-extrabold tracking-tight text-white">
						Dokumen & Tahapan Kerja RIPRID
					</h2>
					<p class="text-xs sm:text-sm text-slate-400 mt-1">
						Klik pada setiap kartu untuk langsung mengakses naskah kerja dan basis data perencanaan di tab baru.
					</p>
				</div>
				<div class="text-xs font-semibold text-sky-300 bg-[#111c33] px-3.5 py-1.5 rounded-full border border-sky-500/30 shrink-0 self-start sm:self-auto shadow-xs">
					Terintegrasi Google & Figma
				</div>
			</div>

			<!-- ROW 1: 3 CARDS (TAHAP 1, 2, 3) -->
			<div class="grid grid-cols-1 md:grid-cols-3 gap-6">
				{#each mainDocuments as doc}
					<div
						class="group relative rounded-3xl bg-gradient-to-b from-[#142038] via-[#101a2f] to-[#0c1527] hover:from-[#192847] hover:via-[#132039] hover:to-[#0f1a30] border-2 border-sky-500/30 hover:border-sky-400/70 p-6 sm:p-7 transition-all duration-300 shadow-xl shadow-black/60 hover:shadow-2xl hover:shadow-sky-900/40 hover:-translate-y-1.5 flex flex-col justify-between overflow-hidden ring-1 ring-white/5"
					>
						<!-- Top Decorative Accent Line -->
						<div class="pointer-events-none absolute top-0 left-0 right-0 h-1 bg-gradient-to-r from-transparent via-sky-400/70 to-transparent opacity-60 group-hover:opacity-100 transition-opacity"></div>
						
						<!-- Ambient Radial Glow inside Card -->
						<div class="pointer-events-none absolute -top-20 -right-20 w-48 h-48 bg-gradient-to-br from-sky-500/20 via-blue-600/15 to-transparent rounded-full blur-2xl group-hover:scale-125 transition-transform duration-500"></div>

						<div class="relative z-10 space-y-5">
							<!-- Card Top Bar: Step Pill & Platform Tag -->
							<div class="flex items-center justify-between gap-2">
								<span class="inline-flex items-center gap-1.5 text-[11px] font-bold px-2.5 py-1 rounded-full bg-[#1b2b4a] border border-sky-400/40 text-sky-300 shadow-2xs">
									<span class="w-1.5 h-1.5 rounded-full bg-sky-400"></span>
									<span>{doc.step}</span>
								</span>

								<span class="text-[11px] font-semibold px-2.5 py-1 rounded-full {doc.platformColor} border shadow-2xs">
									{doc.platform}
								</span>
							</div>

							<!-- Icon & Headings -->
							<div class="space-y-3">
								<div class="w-13 h-13 rounded-2xl bg-[#1b2b4a] border border-sky-400/40 shadow-md shadow-sky-950/40 flex items-center justify-center text-2xl group-hover:scale-105 group-hover:border-sky-300 transition-all duration-300">
									{doc.icon}
								</div>

								<div>
									<h3 class="text-xl font-bold text-white group-hover:text-sky-300 transition-colors tracking-tight leading-snug">
										{doc.title}
									</h3>
									<p class="text-xs font-semibold text-sky-400/90 mt-0.5">
										{doc.subtitle}
									</p>
								</div>

								<p class="text-xs sm:text-sm text-slate-300 leading-relaxed font-normal">
									{doc.description}
								</p>
							</div>

							<!-- Highlights Chips -->
							<div class="space-y-2 pt-1 border-t border-sky-500/20">
								<span class="text-[10px] font-bold uppercase tracking-wider text-sky-400 block">
									Komponen Utama:
								</span>
								<div class="space-y-1.5">
									{#each doc.highlights as hl}
										<div class="flex items-center gap-2 text-xs text-slate-100 font-medium bg-[#0a1120]/90 px-2.5 py-1 rounded-lg border border-sky-500/20">
											<span class="text-sky-400 text-[10px]">✔</span>
											<span class="truncate">{hl}</span>
										</div>
									{/each}
								</div>
							</div>
						</div>

						<!-- Card Action Footer -->
						<div class="relative z-10 pt-5 mt-6 border-t border-sky-500/20 flex items-center justify-between gap-3">
							<span class="text-[11px] font-semibold text-emerald-300 bg-emerald-950/90 px-2.5 py-0.5 rounded-full border border-emerald-700/80 shadow-xs">
								{doc.status}
							</span>

							<a
								href={doc.href}
								target="_blank"
								rel="noopener noreferrer"
								class="inline-flex items-center gap-1.5 px-4 py-2 rounded-full bg-gradient-to-r from-sky-500 to-blue-600 hover:from-sky-400 hover:to-blue-500 text-white text-xs font-bold transition-all shadow-md shadow-sky-900/50 hover:shadow-lg hover:shadow-sky-900/70 hover:scale-105 active:scale-95 cursor-pointer no-underline"
							>
								<span>{doc.ctaLabel}</span>
								<span class="text-xs">↗</span>
							</a>
						</div>
					</div>
				{/each}
			</div>

			<!-- ROW 2: 2 WIDE FEATURED CARDS (TAHAP 4 & TAHAP 5 - CORE DRAF RANWAL) -->
			<div class="space-y-4 pt-4">
				<div class="flex items-center gap-2 pb-1">
					<span class="w-2.5 h-2.5 rounded-full bg-sky-400"></span>
					<h3 class="text-sm font-bold uppercase tracking-widest text-sky-400">
						Naskah Dokumen Ranwal (Rancangan Awal)
					</h3>
				</div>

				<div class="grid grid-cols-1 md:grid-cols-2 gap-6">
					{#each draftDocuments as doc}
						<div
							class="group relative rounded-3xl bg-gradient-to-b from-[#142038] via-[#101a2f] to-[#0c1527] hover:from-[#192847] hover:via-[#132039] hover:to-[#0f1a30] border-2 border-sky-500/35 hover:border-sky-400/75 p-7 sm:p-8 transition-all duration-300 shadow-xl shadow-black/60 hover:shadow-2xl hover:shadow-sky-900/40 hover:-translate-y-1.5 flex flex-col justify-between overflow-hidden ring-1 ring-white/5"
						>
							<!-- Highlight Top Line with Vibrant Sky Tint -->
							<div class="pointer-events-none absolute top-0 left-0 right-0 h-1 bg-gradient-to-r from-sky-400 via-blue-500 to-sky-400 opacity-70 group-hover:opacity-100 transition-opacity"></div>

							<!-- Ambient Soft Glow -->
							<div class="pointer-events-none absolute -bottom-16 -right-16 w-56 h-56 bg-sky-500/15 rounded-full blur-3xl group-hover:scale-125 transition-transform duration-500"></div>

							<div class="relative z-10 space-y-5">
								<!-- Top Bar -->
								<div class="flex items-center justify-between gap-3">
									<div class="flex items-center gap-2">
										<span class="text-xs font-bold px-3 py-1 rounded-full bg-[#1b2b4a] border border-sky-400/40 text-sky-300 shadow-2xs">
											{doc.step}
										</span>
										<span class="text-xs font-semibold px-3 py-1 rounded-full {doc.platformColor} border shadow-2xs">
											{doc.platform}
										</span>
									</div>

									<span
										class="text-xs font-bold px-3 py-1 rounded-full {doc.status === 'Final'
											? 'bg-emerald-950/90 text-emerald-300 border border-emerald-700/80 shadow-xs'
											: 'bg-amber-950/90 text-amber-300 border border-amber-700/80 shadow-xs'}"
									>
										{doc.status}
									</span>
								</div>

								<!-- Headings & Content -->
								<div class="flex items-start gap-4">
									<div class="w-14 h-14 rounded-2xl bg-[#1b2b4a] border border-sky-400/40 shadow-md shadow-sky-950/40 flex items-center justify-center text-3xl shrink-0 group-hover:scale-105 group-hover:border-sky-300 transition-all duration-300">
										{doc.icon}
									</div>

									<div class="space-y-1">
										<h4 class="text-2xl font-bold text-white group-hover:text-sky-300 transition-colors tracking-tight">
											{doc.title}
										</h4>
										<p class="text-xs font-semibold text-sky-400/90">
											{doc.subtitle}
										</p>
									</div>
								</div>

								<p class="text-xs sm:text-sm text-slate-300 leading-relaxed font-normal">
									{doc.description}
								</p>

								<!-- Highlights Badges -->
								<div class="grid grid-cols-1 sm:grid-cols-3 gap-2 pt-2">
									{#each doc.highlights as hl}
										<div class="p-2 rounded-xl bg-[#0a1120]/90 border border-sky-500/20 text-center">
											<div class="text-[10px] text-sky-400 font-bold uppercase tracking-wider">Materi</div>
											<div class="text-xs font-semibold text-slate-100 truncate mt-0.5">{hl}</div>
										</div>
									{/each}
								</div>
							</div>

							<!-- Action Footer -->
							<div class="relative z-10 pt-6 mt-6 border-t border-sky-500/20 flex flex-col sm:flex-row items-center justify-between gap-4">
								<div class="text-xs text-slate-300 font-medium">
									Tautan Langsung Google Docs Cloud
								</div>

								<a
									href={doc.href}
									target="_blank"
									rel="noopener noreferrer"
									class="w-full sm:w-auto inline-flex items-center justify-center gap-2 px-6 py-2.5 rounded-full bg-gradient-to-r from-sky-500 to-blue-600 hover:from-sky-400 hover:to-blue-500 text-white text-xs font-bold transition-all shadow-md shadow-sky-900/50 hover:shadow-lg hover:shadow-sky-900/70 hover:scale-105 active:scale-95 cursor-pointer no-underline"
								>
									<span>{doc.ctaLabel}</span>
									<span class="text-sm">↗</span>
								</a>
							</div>
						</div>
					{/each}
				</div>
			</div>

			<!-- ROW 3: UTILITY & SUPPORT CARDS (REFERENSI DRIVE & KONSULTASI WHATSAPP) -->
			<div class="pt-6 grid grid-cols-1 md:grid-cols-2 gap-6">
				<!-- Referensi Regulasi Card -->
				<div
					class="relative rounded-3xl bg-gradient-to-b from-[#142038] via-[#101a2f] to-[#0c1527] border-2 border-sky-500/30 hover:border-sky-400/60 p-6 sm:p-7 shadow-xl shadow-black/60 flex flex-col justify-between transition-all group ring-1 ring-white/5"
				>
					<div class="space-y-4">
						<div class="flex items-center justify-between">
							<span class="text-[11px] font-bold px-2.5 py-1 rounded-full bg-[#1b2b4a] border border-sky-400/40 text-sky-300">
								Pustaka Regulasi
							</span>
							<span class="text-xs font-semibold text-sky-300 bg-sky-950/80 px-2.5 py-0.5 rounded-full border border-sky-700/80">
								Google Drive
							</span>
						</div>

						<div class="flex items-start gap-4">
							<div class="w-12 h-12 rounded-2xl bg-[#1b2b4a] border border-sky-400/40 flex items-center justify-center text-2xl shadow-xs group-hover:scale-105 transition-transform">
								📚
							</div>
							<div>
								<h4 class="text-lg font-bold text-white group-hover:text-sky-300 transition-colors">
									Referensi & Regulasi Acuan
								</h4>
								<p class="text-xs text-slate-400 mt-1 leading-relaxed">
									Kumpulan dasar hukum, pedoman teknis BRIN, UU riset daerah, dan dokumen RPJMD Kota Sungai Penuh.
								</p>
							</div>
						</div>
					</div>

					<div class="pt-5 mt-5 border-t border-sky-500/20 flex items-center justify-between">
						<span class="text-xs text-slate-300">Folder Berkas Pendukung</span>
						<a
							href={referensiLink}
							target="_blank"
							rel="noopener noreferrer"
							class="inline-flex items-center gap-1.5 text-xs font-bold text-sky-300 hover:text-white bg-[#1b2b4a] hover:bg-sky-600 px-4 py-2 rounded-full border border-sky-400/40 transition-colors no-underline shadow-xs"
						>
							<span>Buka Folder Referensi</span>
							<span>↗</span>
						</a>
					</div>
				</div>

				<!-- Konsultasi WhatsApp Card -->
				<div
					class="relative rounded-3xl bg-gradient-to-b from-[#0e2722] via-[#091f1b] to-[#061513] border-2 border-emerald-500/35 hover:border-emerald-400/70 p-6 sm:p-7 shadow-xl shadow-black/60 flex flex-col justify-between transition-all group ring-1 ring-white/5"
				>
					<div class="space-y-4">
						<div class="flex items-center justify-between">
							<span class="text-[11px] font-bold px-2.5 py-1 rounded-full bg-[#143831] border border-emerald-400/40 text-emerald-300">
								Layanan Konsultasi
							</span>
							<span class="inline-flex items-center gap-1.5 text-xs font-semibold text-emerald-300 bg-emerald-950/80 px-2.5 py-0.5 rounded-full border border-emerald-700/80">
								<span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-pulse"></span>
								<span>Online Chat</span>
							</span>
						</div>

						<div class="flex items-start gap-4">
							<div class="w-12 h-12 rounded-2xl bg-[#143831] border border-emerald-400/40 flex items-center justify-center text-emerald-400 shadow-xs group-hover:scale-105 transition-transform">
								<svg class="w-6 h-6 fill-current" viewBox="0 0 24 24">
									<path
										d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946.003-6.556 5.338-11.891 11.893-11.891 3.181.001 6.167 1.24 8.413 3.488 2.245 2.248 3.481 5.236 3.48 8.414-.003 6.557-5.338 11.892-11.893 11.892-1.99-.001-3.951-.5-5.688-1.448l-6.305 1.654zm6.597-3.807c1.676.995 3.276 1.591 5.392 1.592 5.448 0 9.886-4.434 9.889-9.885.002-5.462-4.415-9.89-9.881-9.892-5.452 0-9.887 4.434-9.889 9.884-.001 2.225.651 3.891 1.746 5.634l-.999 3.648 3.742-.981zm11.387-5.464c-.074-.124-.272-.198-.57-.347-.297-.149-1.758-.868-2.031-.967-.272-.099-.47-.149-.669.149-.198.297-.768.967-.941 1.165-.173.198-.347.223-.644.074-.297-.149-1.255-.462-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.297-.347.446-.521.151-.172.2-.296.3-.495.099-.198.05-.372-.025-.521-.075-.148-.669-1.611-.916-2.206-.242-.579-.487-.501-.669-.51l-.57-.01c-.198 0-.52.074-.792.372s-1.04 1.016-1.04 2.479 1.065 2.876 1.213 3.074c.149.198 2.095 3.2 5.076 4.487.709.306 1.263.489 1.694.626.712.226 1.36.194 1.872.118.571-.085 1.758-.719 2.006-1.413.248-.695.248-1.29.173-1.414z"
									/>
								</svg>
							</div>
							<div>
								<h4 class="text-lg font-bold text-white group-hover:text-emerald-400 transition-colors">
									Konsultasi & Tanya Jawab
								</h4>
								<p class="text-xs text-slate-400 mt-1 leading-relaxed">
									Terhubung langsung dengan tim penyusun Bapperida untuk koordinasi data dan diskusi rancangan RIPRID.
								</p>
							</div>
						</div>
					</div>

					<div class="pt-5 mt-5 border-t border-emerald-500/20 flex items-center justify-between">
						<span class="text-xs text-slate-300">Respon Cepat Tim Bapperida</span>
						<a
							href={waLink}
							target="_blank"
							rel="noopener noreferrer"
							class="inline-flex items-center gap-1.5 text-xs font-bold text-white bg-emerald-600 hover:bg-emerald-500 px-4 py-2 rounded-full shadow-md shadow-emerald-950/50 transition-all no-underline"
						>
							<span>Kirim Pesan WhatsApp</span>
							<span>↗</span>
						</a>
					</div>
				</div>
			</div>
		</section>

		<!-- Bottom Closing Banner (Dark Minimalist Mode) -->
		<section class="relative rounded-3xl bg-gradient-to-b from-[#142038] via-[#101a2f] to-[#0c1527] border-2 border-sky-500/30 p-8 sm:p-12 text-center space-y-4 shadow-xl shadow-black/60 overflow-hidden ring-1 ring-white/5">
			<div class="pointer-events-none absolute top-0 left-0 right-0 h-1 bg-gradient-to-r from-transparent via-sky-400/60 to-transparent"></div>

			<div class="inline-flex items-center gap-2 px-3.5 py-1 rounded-full text-[11px] font-bold bg-[#1b2b4a] text-sky-300 border border-sky-400/40 shadow-2xs">
				<span>🏛️</span>
				<span>Sinergi Perencanaan Daerah</span>
			</div>

			<h3 class="text-2xl sm:text-3xl font-extrabold text-white tracking-tight">
				Mewujudkan Kebijakan Berbasis Bukti Ilmiah
			</h3>

			<p class="text-xs sm:text-sm text-slate-300 max-w-xl mx-auto leading-relaxed font-normal">
				Penyusunan Rencana Induk Penelitian Riset dan Inovasi (RIPRID) merupakan langkah konkret Bapperida Kota Sungai Penuh dalam memperkuat ekosistem inovasi untuk percepatan kesejahteraan masyarakat.
			</p>
		</section>
	</main>

	<!-- Footer with Clean Dark Slate Line -->
	<footer class="border-t border-slate-800/80 bg-[#050811] py-10">
		<div class="max-w-6xl mx-auto px-6 flex flex-col sm:flex-row items-center justify-between gap-4 text-xs text-slate-400">
			<div class="flex items-center gap-2">
				<span class="text-slate-200 font-bold">Bapperida Kota Sungai Penuh</span>
				<span>•</span>
				<span>RIPRID 2027–2029</span>
			</div>
			<div class="text-slate-400 font-medium">
				uji coba rindra aniko
			</div>
		</div>
	</footer>
</div>
