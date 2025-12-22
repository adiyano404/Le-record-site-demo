# Le-record-site-demo
Le record - Guinee land registry demo
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Le Record – Guinea Land &amp; Property Registry</title>
  <meta name="description" content="Le Record – bilingual concept app for Guinea's national land and home registry, with regions, prefectures, PostgreSQL + Django backend design, and Orange Money payment flows." />

  <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>

  <style>
    html {
      scroll-behavior: smooth;
    }
  </style>
</head>
<body class="bg-slate-950 text-slate-50">
  <div class="min-h-screen flex flex-col">
    <!-- Header / Navigation -->
    <header class="border-b border-slate-900 bg-slate-950/80 backdrop-blur">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 py-4 flex items-center justify-between gap-4">
        <div class="flex items-center gap-3">
          <div class="h-9 w-9 rounded-lg bg-emerald-500 flex items-center justify-center text-slate-900 font-black text-lg">
            LR
          </div>
          <div>
            <div class="font-semibold tracking-tight text-slate-100" data-i18n="brand.name">Le Record</div>
            <div class="text-xs text-slate-400" data-i18n="brand.tagline">Guinea Digital Land &amp; Property Registry</div>
          </div>
        </div>
        <nav class="hidden md:flex items-center gap-6 text-sm text-slate-100">
          <a href="#hero" class="hover:text-emerald-400" data-i18n="nav.home">Home</a>
          <a href="#accounts" class="hover:text-emerald-400" data-i18n="nav.accounts">Account &amp; Access</a>
          <a href="#search-section" class="hover:text-emerald-400" data-i18n="nav.search">Search &amp; Verify</a>
          <a href="#reports" class="hover:text-emerald-400" data-i18n="nav.reports">Reports &amp; Pricing</a>
          <a href="#developers" id="navDevelopersLink" class="hover:text-emerald-400 hidden" data-i18n="nav.developers">Technical Design</a>
          <a href="#divisions" class="hover:text-emerald-400" data-i18n="nav.divisions">Regions &amp; Prefectures</a>
          <a href="#about" class="hover:text-emerald-400" data-i18n="nav.about">About</a>
        </nav>
        <div class="flex items-center gap-2">
          <span id="adminBadge" class="hidden sm:inline-flex items-center text-[10px] px-2 py-0.5 rounded-full bg-emerald-500/10 border border-emerald-500/50 text-emerald-300 font-semibold tracking-tight uppercase">Admin</span>
          <div class="hidden sm:flex items-center gap-1 text-xs border border-slate-800 rounded-full px-1.5 py-0.5 bg-slate-900">
            <span class="px-1 text-slate-400" data-i18n="common.language">Language</span>
            <button id="lang-en" class="px-2 py-0.5 rounded-full text-emerald-300 bg-emerald-500/15 border border-emerald-500/40 text-[11px] font-medium">EN</button>
            <button id="lang-fr" class="px-2 py-0.5 rounded-full text-slate-400 hover:text-emerald-300 text-[11px] font-medium">FR</button>
          </div>
          <button id="headerAccountBtn" class="hidden sm:inline-flex text-xs px-3 py-1.5 rounded-full border border-emerald-500/60 text-emerald-300 hover:bg-emerald-500/10 transition" data-i18n="nav.login">
            Sign in (demo)
          </button>
          <button class="sm:hidden inline-flex items-center justify-center border border-slate-700 rounded-md h-9 w-9" aria-label="Open navigation">
            <svg class="h-4 w-4 text-slate-300" viewBox="0 0 20 20" fill="none" aria-hidden="true">
              <path d="M3 6h14M3 10h14M3 14h14" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" />
            </svg>
          </button>
        </div>
      </div>
    </header>

    <main class="flex-1">
      <!-- Hero -->
      <section id="hero" class="border-b border-slate-900 bg-gradient-to-b from-slate-950 via-slate-950 to-slate-900">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 py-12 sm:py-16 lg:py-20 grid lg:grid-cols-[minmax(0,1.3fr)_minmax(0,1fr)] gap-10 items-center">
          <div class="space-y-4">
            <p class="text-xs font-medium tracking-wide text-emerald-300 uppercase" data-i18n="hero.eyebrow">Republic of Guinea · Ministry of Urban Planning &amp; Housing</p>
            <h1 class="text-2xl sm:text-3xl lg:text-4xl font-semibold tracking-tight text-slate-50" data-i18n="hero.title">
              One registry for every parcel and home in Guinea’s four natural regions.
            </h1>
            <p class="text-sm text-slate-200 max-w-xl" data-i18n="hero.subtitle">
              Le Record, a data company with the sole objectives of searching properties, deeds and transactions records across Basse-Guinée, Moyenne-Guinée, Haute-Guinée and Guinée Forestière, with secure public verification.
            </p>
            <div class="flex flex-wrap gap-3 pt-2">
              <a href="#search-section" class="inline-flex items-center justify-center px-4 py-2 rounded-lg bg-emerald-500 text-slate-950 text-sm font-semibold hover:bg-emerald-400 transition" data-i18n="hero.primaryCta">
                Search the registry
              </a>
              <a href="#developers" id="heroTechCta" class="inline-flex items-center justify-center px-4 py-2 rounded-lg border border-slate-700 text-sm font-semibold text-slate-100 hover:border-emerald-400 hover:text-emerald-300 transition hidden" data-i18n="hero.secondaryCta">
                See technical design
              </a>
            </div>
            <div class="flex flex-wrap items-center gap-3 pt-3 text-[11px] text-slate-400">
              <div class="inline-flex items-center gap-1">
                <span class="h-2 w-2 rounded-full bg-emerald-400"></span>
                <span data-i18n="hero.badgeAccounts">Users must create an account to search and order official reports.</span>
              </div>
              <div class="inline-flex items-center gap-1 text-slate-500">
                <span>PostgreSQL</span>
                <span>·</span>
                <span>Django REST Framework</span>
                <span>·</span>
                <span>Orange Money</span>
              </div>
            </div>
          </div>
          <div class="bg-slate-900/80 border border-slate-800 rounded-2xl p-5 sm:p-6 space-y-4">
            <h2 class="text-sm font-semibold text-emerald-300" data-i18n="hero.sideTitle">Registry, billing and payments in one platform</h2>
            <ul class="text-xs text-slate-300 space-y-2">
              <li data-i18n="hero.sidePoint1">
                Land registry core: parcels, owners, ownerships, transactions, disputes and documents modeled in PostgreSQL.
              </li>
              <li data-i18n="hero.sidePoint2">
                Monetization: products, orders, payments and signed reports managed by a dedicated billing app.
              </li>
              <li data-i18n="hero.sidePoint3">
                Payments: Orange Money as primary mobile money provider, extendable to cards, bank transfer and cash at offices.
              </li>
            </ul>
            <div class="border border-slate-800 rounded-xl p-3 text-[11px] text-slate-300 bg-slate-950/60">
              <p class="font-semibold mb-1" data-i18n="hero.demoLabel">Demo only</p>
              <p data-i18n="hero.demoBody">
                This page is a front-end concept. In production all data and permissions come from a secured Django + PostgreSQL backend operated by the Government of Guinea.
              </p>
            </div>
          </div>
        </div>
      </section>

      <!-- Accounts & Access -->
      <section id="accounts" class="border-b border-slate-900 bg-slate-950">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 py-10 sm:py-14 lg:py-16 grid lg:grid-cols-[minmax(0,1.2fr)_minmax(0,1.1fr)] gap-8 items-start">
          <div class="space-y-4">
            <div>
              <h2 class="text-xl sm:text-2xl font-semibold tracking-tight mb-1 text-slate-50" data-i18n="accounts.sectionTitle">Create an account to search the registry</h2>
              <p class="text-sm text-slate-300" data-i18n="accounts.sectionSubtitle">
                For transparency and security, users, professionals and ministries must authenticate before they can search parcels or add property records.
              </p>
            </div>
            <div class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5">
              <div class="flex border-b border-slate-800 mb-4 text-sm">
                <button id="account-tab-signin" class="flex-1 py-2 text-center border-b-2 border-emerald-500 text-emerald-300 font-medium" data-i18n="accounts.signInTab">Sign in</button>
                <button id="account-tab-signup" class="flex-1 py-2 text-center border-b-2 border-transparent text-slate-400 hover:text-emerald-300" data-i18n="accounts.signUpTab">Create account</button>
              </div>

              <div class="space-y-3 mb-3">
                <p id="authStatusText" class="text-xs text-emerald-300"></p>
                <p class="text-[11px] text-slate-400" data-i18n="accounts.demoAdminHint">
                  Demo: sign in with username “admin” and password “admin” to manage ministry permissions.
                </p>
                <button
                  id="simulateVerifyBtn"
                  type="button"
                  class="hidden inline-flex items-center px-2 py-1 rounded-md border border-emerald-500/60 text-[11px] text-emerald-300 hover:bg-emerald-500/10 transition"
                  data-i18n="accounts.simulateVerifyButton"
                >
                  Mark account as verified (demo)
                </button>
              </div>

              <!-- Sign in form -->
              <form id="signInForm" class="space-y-3">
                <div>
                  <label for="signInUsername" class="block text-xs text-slate-300 mb-1" data-i18n="accounts.usernameLabel">Username</label>
                  <input id="signInUsername" type="text" class="w-full bg-slate-950 border border-slate-700 rounded-lg px-3 py-1.5 text-xs text-slate-50 placeholder-slate-500 focus:outline-none focus:ring-1 focus:ring-emerald-500" />
                </div>
                <div>
                  <label for="signInPassword" class="block text-xs text-slate-300 mb-1" data-i18n="accounts.passwordLabel">Password</label>
                  <input id="signInPassword" type="password" class="w-full bg-slate-950 border border-slate-700 rounded-lg px-3 py-1.5 text-xs text-slate-50 placeholder-slate-500 focus:outline-none focus:ring-1 focus:ring-emerald-500" />
                </div>
                <p id="signInError" class="text-[11px] text-amber-300 min-h-[1rem]"></p>
                <div class="flex items-center gap-2">
                  <button type="submit" class="inline-flex items-center justify-center px-3 py-1.5 rounded-lg bg-emerald-500 text-slate-950 text-xs font-semibold hover:bg-emerald-400 transition" data-i18n="accounts.signInButton">
                    Sign in
                  </button>
                  <button id="signOutBtn" type="button" class="hidden inline-flex items-center justify-center px-3 py-1.5 rounded-lg border border-slate-600 text-slate-200 text-xs font-semibold hover:border-emerald-400 transition" data-i18n="accounts.signOutButton">
                    Sign out
                  </button>
                </div>
              </form>

              <!-- Sign up form -->
              <form id="signUpForm" class="space-y-3 hidden mt-3">
                <div>
                  <label for="signUpUsername" class="block text-xs text-slate-300 mb-1" data-i18n="accounts.usernameLabel">Username</label>
                  <input id="signUpUsername" type="text" class="w-full bg-slate-950 border border-slate-700 rounded-lg px-3 py-1.5 text-xs text-slate-50 placeholder-slate-500 focus:outline-none focus:ring-1 focus:ring-emerald-500" />
                </div>
                <div class="grid sm:grid-cols-2 gap-3">
                  <div>
                    <label for="signUpPassword" class="block text-xs text-slate-300 mb-1" data-i18n="accounts.passwordLabel">Password</label>
                    <input id="signUpPassword" type="password" class="w-full bg-slate-950 border border-slate-700 rounded-lg px-3 py-1.5 text-xs text-slate-50 placeholder-slate-500 focus:outline-none focus:ring-1 focus:ring-emerald-500" />
                  </div>
                  <div>
                    <label for="signUpEmail" class="block text-xs text-slate-300 mb-1" data-i18n="accounts.emailLabel">Email</label>
                    <input id="signUpEmail" type="email" class="w-full bg-slate-950 border border-slate-700 rounded-lg px-3 py-1.5 text-xs text-slate-50 placeholder-slate-500 focus:outline-none focus:ring-1 focus:ring-emerald-500" />
                  </div>
                </div>
                <div class="grid sm:grid-cols-2 gap-3">
                  <div>
                    <label for="signUpPhone" class="block text-xs text-slate-300 mb-1" data-i18n="accounts.phoneLabel">Mobile phone</label>
                    <input id="signUpPhone" type="tel" class="w-full bg-slate-950 border border-slate-700 rounded-lg px-3 py-1.5 text-xs text-slate-50 placeholder-slate-500 focus:outline-none focus:ring-1 focus:ring-emerald-500" />
                  </div>
                  <div>
                    <label for="signUpUserType" class="block text-xs text-slate-300 mb-1" data-i18n="accounts.userTypeLabel">Account type</label>
                    <select id="signUpUserType" class="w-full bg-slate-950 border border-slate-700 rounded-lg px-3 py-1.5 text-xs focus:outline-none focus:ring-1 focus:ring-emerald-500">
                      <option value="INDIVIDUAL" data-i18n="accounts.userTypeIndividual">Individual user</option>
                      <option value="PROFESSIONAL" data-i18n="accounts.userTypeProfessional">Professional (notary, surveyor, banker…)</option>
                      <option value="INSTITUTION" data-i18n="accounts.userTypeInstitution">Institution / company</option>
                      <option value="STAFF" data-i18n="accounts.userTypeStaff">Government staff</option>
                    </select>
                  </div>
                </div>
                <div>
                  <label for="signUpOrg" class="block text-xs text-slate-300 mb-1" data-i18n="accounts.organizationLabel">Organization / ministry (if applicable)</label>
                  <input id="signUpOrg" type="text" class="w-full bg-slate-950 border border-slate-700 rounded-lg px-3 py-1.5 text-xs text-slate-50 placeholder-slate-500 focus:outline-none focus:ring-1 focus:ring-emerald-500" />
                </div>
                <div class="grid sm:grid-cols-2 gap-3">
                  <div class="flex items-center gap-2 text-[11px] text-slate-300">
                    <input id="signUpMinistryWorker" type="checkbox" class="h-3 w-3 rounded border-slate-600 bg-slate-950" />
                    <label for="signUpMinistryWorker" data-i18n="accounts.ministryWorkerLabel">I work for a ministry or public agency</label>
                  </div>
                  <div class="text-[11px] text-slate-300">
                    <span class="block mb-1" data-i18n="accounts.verifyByLabel">Choose how to verify your account:</span>
                    <div class="flex items-center gap-3">
                      <label class="inline-flex items-center gap-1">
                        <input type="radio" name="signUpVerifyMethod" value="email" class="h-3 w-3 rounded border-slate-600 bg-slate-950" checked />
                        <span data-i18n="accounts.verifyByEmail">Email link</span>
                      </label>
                      <label class="inline-flex items-center gap-1">
                        <input type="radio" name="signUpVerifyMethod" value="sms" class="h-3 w-3 rounded border-slate-600 bg-slate-950" />
                        <span data-i18n="accounts.verifyBySms">SMS code</span>
                      </label>
                    </div>
                  </div>
                </div>
                <div class="flex items-center gap-2 text-[11px] text-slate-300">
                  <input id="signUpHumanCheck" type="checkbox" class="h-3 w-3 rounded border-slate-600 bg-slate-950" />
                  <label for="signUpHumanCheck" data-i18n="accounts.humanCheckLabel">I confirm that I am a human user and not an automated bot.</label>
                </div>
                <p id="signUpError" class="text-[11px] text-amber-300 min-h-[1rem]"></p>
                <button type="submit" class="inline-flex items-center justify-center px-3 py-1.5 rounded-lg bg-emerald-500 text-slate-950 text-xs font-semibold hover:bg-emerald-400 transition" data-i18n="accounts.signUpButton">
                  Create account
                </button>
              </form>
            </div>
          </div>

          <!-- Ministries & registry access -->
          <div class="space-y-4">
            <div class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5">
              <h3 class="text-sm font-semibold text-emerald-300 mb-2" data-i18n="admin.ministriesTitle">Ministries &amp; agencies with registry access</h3>
              <p class="text-xs text-slate-300 mb-3" data-i18n="admin.ministriesIntro">
                In production, only authorized ministries and agencies can create or update property records. This demo lets an administrator toggle who may add parcels and transactions.
              </p>
              <div id="ministriesContainer" class="space-y-2 text-[11px] text-slate-200"></div>
            </div>
          </div>
        </div>
      </section>

      <!-- Search & Verification -->
      <section id="search-section" class="border-b border-slate-900 bg-slate-950">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 py-10 sm:py-14 lg:py-16">
          <div class="mb-6 sm:mb-8 flex flex-col sm:flex-row sm:items-end justify-between gap-4">
            <div>
              <h2 class="text-xl sm:text-2xl font-semibold tracking-tight mb-1 text-slate-50" data-i18n="search.sectionTitle">Public search &amp; verification</h2>
              <p class="text-sm text-slate-200 max-w-2xl" data-i18n="search.sectionDesc">
                After signing in, look up parcels and transactions to verify land information before buying, selling or requesting official reports.
              </p>
            </div>
            <div class="flex items-center gap-2 text-xs text-slate-400">
              <span class="inline-flex h-2 w-2 rounded-full bg-amber-400"></span>
              <span data-i18n="search.demoNotice">Mock data only – no real parcels or owners are loaded.</span>
            </div>
          </div>

          <div class="space-y-4 mb-6">
            <div id="searchGate" class="bg-slate-900/80 border border-amber-500/40 rounded-xl p-4 sm:p-5">
              <h3 id="searchGateTitle" class="text-sm font-semibold text-amber-300 mb-1" data-i18n="search.loginRequiredTitle">Account required</h3>
              <p id="searchGateBody" class="text-xs text-slate-200 mb-2" data-i18n="search.loginRequiredBody">
                Create an account or sign in to use the public registry search in this demo.
              </p>
              <a href="#accounts" class="inline-flex items-center px-3 py-1.5 rounded-lg bg-emerald-500 text-slate-950 text-xs font-semibold hover:bg-emerald-400 transition" data-i18n="search.loginRequiredCta">
                Go to account section
              </a>
            </div>
          </div>

          <div id="searchInner" class="grid lg:grid-cols-[minmax(0,1.2fr)_minmax(0,1fr)] gap-8 items-start">
            <!-- Left: Search panels -->
            <div class="space-y-4">
              <div class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5">
                <div class="flex border-b border-slate-800 mb-4 text-sm">
                  <button id="tab-parcel" class="flex-1 py-2 text-center border-b-2 border-emerald-500 text-emerald-300 font-medium" data-i18n="search.parcelTab">Parcel</button>
                  <button id="tab-transaction" class="flex-1 py-2 text-center border-b-2 border-transparent text-slate-400 hover:text-emerald-300" data-i18n="search.transactionTab">Transaction</button>
                </div>
                <div id="parcel-search-panel" class="space-y-3">
                  <label for="parcelInput" class="text-xs font-medium text-slate-300" data-i18n="search.parcelPlaceholder">Example: GN-4-2023-000001</label>
                  <div class="flex flex-col sm:flex-row gap-3">
                    <input id="parcelInput" type="text" class="flex-1 bg-slate-950 border border-slate-700 rounded-lg px-3 py-2 text-sm text-slate-50 placeholder-slate-500 focus:outline-none focus:ring-1 focus:ring-emerald-500" data-i18n-placeholder="search.parcelPlaceholder" />
                    <button id="parcelSearchBtn" class="inline-flex items-center justify-center px-4 py-2 rounded-lg bg-emerald-500 text-slate-950 text-sm font-semibold hover:bg-emerald-400 transition" data-i18n="search.searchButton">
                      Search
                    </button>
                  </div>
                </div>
                <div id="transaction-search-panel" class="space-y-3 hidden">
                  <label for="transactionInput" class="text-xs font-medium text-slate-300" data-i18n="search.transactionPlaceholder">Example: TXN-2023-000045</label>
                  <div class="flex flex-col sm:flex-row gap-3">
                    <input id="transactionInput" type="text" class="flex-1 bg-slate-950 border border-slate-700 rounded-lg px-3 py-2 text-sm text-slate-50 placeholder-slate-500 focus:outline-none focus:ring-1 focus:ring-emerald-500" data-i18n-placeholder="search.transactionPlaceholder" />
                    <button id="transactionSearchBtn" class="inline-flex items-center justify-center px-4 py-2 rounded-lg bg-emerald-500 text-slate-950 text-sm font-semibold hover:bg-emerald-400 transition" data-i18n="search.searchButton">
                      Search
                    </button>
                  </div>
                </div>
              </div>

              <!-- Result containers -->
              <div id="parcelResultContainer" class="hidden bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5"></div>
              <div id="transactionResultContainer" class="hidden bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5"></div>
            </div>

            <!-- Right: Guidance -->
            <div class="space-y-4">
              <div class="bg-slate-900/80 border border-emerald-500/40 rounded-xl p-4 sm:p-5">
                <h3 class="text-sm font-semibold text-emerald-300 mb-2" data-i18n="search.journeyTitle">3-step user journey</h3>
                <ol class="space-y-2 text-xs text-slate-300 list-decimal list-inside">
                  <li data-i18n="search.journeyStep1">Create an account and pay to search the parcel or transaction.</li>
                  <li data-i18n="search.journeyStep2">Confirm that the information matches paper records and local knowledge.</li>
                  <li data-i18n="search.journeyStep3">Order a certified report when you need legal proof.</li>
                </ol>
                <p class="mt-3 text-[11px] text-slate-400" data-i18n="search.privacyNote">No personal owner identifiers (ID numbers, full private addresses) are exposed in public search.</p>
              </div>
              <div class="bg-slate-900/60 border border-slate-800 rounded-xl p-4 sm:p-5">
                <h3 class="text-sm font-semibold mb-2" data-i18n="search.guineaTitle">Guinea-focused design</h3>
                <ul class="space-y-2 text-xs text-slate-300">
                  <li data-i18n="search.guineaPoint1">• Four natural regions (Basse, Moyenne, Haute, Forestière) and all prefectures encoded with GN + number codes.</li>
                  <li data-i18n="search.guineaPoint2">• Orange Money as the primary payment channel, extendable to cards, bank transfer and cash.</li>
                  <li data-i18n="search.guineaPoint3">• Compatible with cash offices, offline workflows and paper archives.</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Reports & Monetization -->
      <section id="reports" class="border-b border-slate-900 bg-slate-950">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 py-10 sm:py-14 lg:py-16">
          <div class="max-w-3xl mb-6 sm:mb-10">
            <h2 class="text-xl sm:text-2xl font-semibold tracking-tight mb-2" data-i18n="reports.sectionTitle">Monetized reports &amp; extracts</h2>
            <p class="text-sm text-slate-300" data-i18n="reports.sectionDesc">
              Le Record monetizes access to parcel and home records: users pay to research a property or land records for informational or transactional reasons.
            </p>
          </div>

          <div class="grid lg:grid-cols-[minmax(0,1.1fr)_minmax(0,1.1fr)] gap-8 items-start">
            <!-- Products -->
            <div class="space-y-4">
              <h3 class="text-sm font-semibold text-slate-200" data-i18n="reports.chooseProduct">Choose a product</h3>
              <div class="grid sm:grid-cols-2 gap-4">
                <!-- Full report -->
                <button id="product-full" type="button" class="group text-left bg-slate-900/80 border border-emerald-500/40 rounded-xl p-4 hover:border-emerald-400 hover:bg-slate-900 transition">
                  <div class="flex items-center justify-between gap-2 mb-1">
                    <span class="text-sm font-semibold text-emerald-300" data-i18n="reports.fullReport">Full Property Report</span>
                    <span class="inline-flex items-center px-2 py-0.5 rounded-full bg-emerald-500/10 text-[11px] text-emerald-300 border border-emerald-500/40" data-i18n="reports.price">Price</span>
                  </div>
                  <p class="text-xs text-slate-300 mb-2" data-i18n="reports.fullReportDesc">
                    Complete history of the parcel, owners, transactions and linked documents.
                  </p>
                  <p class="text-[11px] text-slate-400">≈ 100 000 GNF / report (configurable)</p>
                </button>

                <!-- Certified extract -->
                <button id="product-cert" type="button" class="group text-left bg-slate-900/60 border border-slate-800 rounded-xl p-4 hover:border-emerald-400 hover:bg-slate-900 transition">
                  <div class="flex items-center justify-between gap-2 mb-1">
                    <span class="text-sm font-semibold text-slate-100" data-i18n="reports.certExtract">Certified Extract</span>
                    <span class="inline-flex items-center px-2 py-0.5 rounded-full bg-slate-800 text-[11px] text-slate-200 border border-slate-700" data-i18n="reports.price">Price</span>
                  </div>
                  <p class="text-xs text-slate-300 mb-2" data-i18n="reports.certExtractDesc">
                    Legally certified extract for notaries, banks and courts.
                  </p>
                  <p class="text-[11px] text-slate-400">≈ 50 000 GNF / extract (configurable)</p>
                </button>
              </div>
              <p class="text-[11px] text-slate-400">
                The exact pricing matrix is stored in the <code class="text-[11px] bg-slate-900 px-1 rounded border border-slate-700">billing_product</code> table and can be updated without code changes.
              </p>
            </div>

            <!-- Order & Payment Simulation -->
            <div class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5 space-y-4">
              <div class="flex items-center justify-between gap-2">
                <div>
                  <h3 class="text-sm font-semibold text-slate-200" data-i18n="reports.orderSummaryTitle">Order summary</h3>
                  <p class="text-[11px] text-slate-400" data-i18n="reports.orderSummaryHint">Uses mock data mapped to the real Django models.</p>
                </div>
                <button id="createOrderBtn" class="inline-flex items-center px-3 py-1.5 rounded-lg bg-emerald-500 text-slate-950 text-xs font-semibold hover:bg-emerald-400 transition" data-i18n="reports.simulateOrder">
                  Create demo order
                </button>
              </div>
              <div id="orderSummary" class="text-xs text-slate-200 space-y-1 min-h-[2.5rem]"></div>

              <div class="pt-3 border-t border-slate-800 space-y-3">
                <h4 class="text-xs font-semibold text-slate-200" data-i18n="reports.payWithOrangeMoney">Pay with Orange Money (demo)</h4>
                <div class="flex flex-col sm:flex-row gap-3 items-center">
                  <div class="flex-1 w-full">
                    <label for="omPhoneInput" class="block text-[11px] text-slate-400 mb-1" data-i18n="reports.phoneLabel">Orange Money phone number</label>
                    <input id="omPhoneInput" type="tel" inputmode="tel" class="w-full bg-slate-950 border border-slate-700 rounded-lg px-3 py-1.5 text-xs text-slate-50 placeholder-slate-500 focus:outline-none focus:ring-1 focus:ring-emerald-500" placeholder="2246XXXXXXX" />
                  </div>
                  <button id="startPaymentBtn" class="inline-flex items-center justify-center px-3 py-1.5 rounded-lg bg-emerald-500 text-slate-950 text-xs font-semibold hover:bg-emerald-400 transition" data-i18n="reports.startPayment">
                    Start payment
                  </button>
                </div>
                <p id="paymentMessage" class="text-[11px] text-amber-300 min-h-[1.2rem]"></p>
                <div>
                  <h5 class="text-[11px] font-semibold text-slate-300 mb-1" data-i18n="reports.paymentTimelineTitle">Payment simulation</h5>
                  <ol id="paymentTimeline" class="space-y-1 text-[11px] text-slate-300"></ol>
                  <div id="sampleReportLinkContainer" class="mt-2 hidden">
                    <a id="sampleReportLink" href="https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf" target="_blank" rel="noopener noreferrer" class="inline-flex items-center gap-1 text-[11px] text-emerald-300 hover:text-emerald-200 underline decoration-emerald-500/70" data-i18n="reports.downloadSampleReport">
                      Open sample report
                    </a>
                  </div>
                  <div id="qrCodeContainer" class="mt-2 hidden">
                    <h6 class="text-[11px] font-semibold text-slate-200 mb-1" data-i18n="reports.qrCodeTitle">Verification QR code (demo)</h6>
                    <div class="flex items-center gap-3">
                      <img id="qrCodeImage" class="h-20 w-20 bg-slate-900 border border-slate-700 rounded" alt="QR code demo" />
                      <p class="text-[11px] text-slate-400" data-i18n="reports.qrCodeHint">
                        In production, scanning this QR code would open an online verification page for this exact parcel or transaction report.
                      </p>
                    </div>
                  </div>
                  <p class="mt-2 text-[10px] text-slate-500" data-i18n="reports.paymentSuccessNote">
                    In production, status is driven entirely by real-time callbacks from Orange Money and the banking gateway.
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Technical Architecture (admin-only, hidden by default) -->
      <section id="developers" class="border-b border-slate-900 bg-slate-950 hidden">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 py-10 sm:py-14 lg:py-16">
          <div class="max-w-3xl mb-6 sm:mb-10">
            <h2 class="text-xl sm:text-2xl font-semibold tracking-tight mb-2" data-i18n="dev.sectionTitle">Technical architecture</h2>
            <p class="text-sm text-slate-300" data-i18n="dev.stackBody">
              Le Record is designed around a robust Django + PostgreSQL backend with a modern API layer, custom accounts, Orange Money integration and data-driven regions and prefectures.
            </p>
          </div>

          <div class="grid lg:grid-cols-3 gap-5">
            <article class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5 space-y-2">
              <h3 class="text-sm font-semibold text-emerald-300" data-i18n="dev.stackTitle">Core stack</h3>
              <ul class="text-xs text-slate-300 space-y-1.5">
                <li data-i18n="dev.stackPoint1">• Django + Django REST Framework with a custom <code class="bg-slate-900 px-1 rounded border border-slate-700">Account</code> user model (users, professionals, institutions, staff).</li>
                <li data-i18n="dev.stackPoint2">• PostgreSQL schema for regions, prefectures, communes, parcels, owners, ownerships, transactions, disputes and documents.</li>
                <li data-i18n="dev.stackPoint3">• Separate <code class="bg-slate-900 px-1 rounded border border-slate-700">billing</code> app for products, orders, payments and generated reports.</li>
              </ul>
            </article>

            <article class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5 space-y-2">
              <h3 class="text-sm font-semibold text-emerald-300" data-i18n="dev.dbTitle">Registry data model (simplified)</h3>
              <p class="text-xs text-slate-300" data-i18n="dev.dbBody">
                Administrative tables store the four natural regions and all prefectures with GN + number codes. Core land tables store parcels, owners, ownership records, transactions, disputes and supporting documents.
              </p>
              <ul class="text-[11px] text-slate-400 space-y-1.5">
                <li data-i18n="dev.dbPoint1">• <strong>ownerships</strong> table tracks current and historical rights per parcel.</li>
                <li data-i18n="dev.dbPoint2">• <strong>transactions</strong> store prices, fees, taxes and registrar decisions.</li>
                <li data-i18n="dev.dbPoint3">• <strong>disputes</strong> flag conflicted parcels and drive public status.</li>
              </ul>
            </article>

            <article class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5 space-y-2">
              <h3 class="text-sm font-semibold text-emerald-300" data-i18n="dev.apiTitle">Public APIs</h3>
              <p class="text-xs text-slate-300" data-i18n="dev.apiBody">
                A Django REST Framework public app exposes read-only APIs for parcel and transaction lookup, plus authenticated endpoints for ordering reports and initiating Orange Money payments.
              </p>
              <dl class="text-[11px] text-slate-300 space-y-1.5 mt-1">
                <div>
                  <dt class="font-semibold" data-i18n="dev.endpointParcel">GET /api/public/parcels/{parcel_number}/</dt>
                  <dd class="text-slate-400" data-i18n="dev.endpointParcelDesc">Parcel lookup + current owner, title and prefecture snapshot.</dd>
                </div>
                <div>
                  <dt class="font-semibold" data-i18n="dev.endpointTransaction">GET /api/public/transactions/{transaction_number}/</dt>
                  <dd class="text-slate-400" data-i18n="dev.endpointTransactionDesc">Transaction type, parties, status and linked parcel.</dd>
                </div>
                <div>
                  <dt class="font-semibold" data-i18n="dev.endpointOrder">POST /api/billing/orders/parcel-report/</dt>
                  <dd class="text-slate-400" data-i18n="dev.endpointOrderDesc">Authenticated creation of a paid order for a parcel or transaction.</dd>
                </div>
                <div>
                  <dt class="font-semibold" data-i18n="dev.endpointPay">POST /api/billing/orders/{order_id}/pay/</dt>
                  <dd class="text-slate-400" data-i18n="dev.endpointPayDesc">Initiate Orange Money or other payments.</dd>
                </div>
              </dl>
            </article>
          </div>

          <div class="mt-5 grid lg:grid-cols-[minmax(0,1.2fr)_minmax(0,1fr)] gap-5">
            <article class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5 space-y-2">
              <h3 class="text-sm font-semibold text-emerald-300" data-i18n="dev.omTitle">Orange Money integration</h3>
              <p class="text-xs text-slate-300" data-i18n="dev.omBody">
                A dedicated payment provider handles Orange Money flows: initiating payments, handling asynchronous webhooks and updating Order and Payment records atomically.
              </p>
              <ol class="text-[11px] text-slate-300 list-decimal list-inside space-y-1.5 mt-2">
                <li data-i18n="dev.omStep1">User or institution creates an <strong>Order</strong> for a product (e.g. FULL_REPORT).</li>
                <li data-i18n="dev.omStep2">The backend creates a <strong>Payment</strong> row and calls the Orange Money API via <code class="bg-slate-900 px-1 rounded border border-slate-700">OrangeMoneyProvider</code>.</li>
                <li data-i18n="dev.omStep3">Orange Money redirects or pushes an STK request to the user’s wallet.</li>
                <li data-i18n="dev.omStep4">The asynchronous webhook updates <strong>Payment.status</strong> and <strong>Order.status</strong> atomically.</li>
                <li data-i18n="dev.omStep5">A background task generates a signed PDF <strong>Report</strong> and stores its URL.</li>
              </ol>
            </article>

            <article class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5 space-y-2">
              <h3 class="text-sm font-semibold text-emerald-300" data-i18n="dev.securityTitle">Security &amp; governance</h3>
              <p class="text-xs text-slate-300" data-i18n="dev.securityBody">
                Role-based access, ministry-level permissions, verified staff accounts, signed reports and immutable transaction logs ensure legal-grade evidence for ownership changes.
              </p>
              <ul class="text-[11px] text-slate-300 space-y-1.5 mt-1">
                <li data-i18n="dev.securityPoint1">• Staff users (registrars, surveyors) onboarded as <code class="bg-slate-900 px-1 rounded border border-slate-700">Account</code> with STAFF type.</li>
                <li data-i18n="dev.securityPoint2">• Ministries and agencies grouped with explicit “can_add_property_records” permissions.</li>
                <li data-i18n="dev.securityPoint3">• Every change to parcels, ownerships or disputes is versioned and auditable.</li>
                <li data-i18n="dev.securityPoint4">• Reports are signed with digital seals and verifiable QR codes.</li>
              </ul>
            </article>
          </div>
        </div>
      </section>

      <!-- Regions & Prefectures -->
      <section id="divisions" class="border-b border-slate-900 bg-slate-950">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 py-10 sm:py-14 lg:py-16">
          <div class="max-w-3xl mb-6 sm:mb-10">
            <h2 class="text-xl sm:text-2xl font-semibold tracking-tight mb-2" data-i18n="divisions.sectionTitle">Regions &amp; prefectures of Guinea</h2>
            <p class="text-sm text-slate-300" data-i18n="divisions.sectionDesc">
              This demo models Guinea with four natural regions – Basse-Guinée, Moyenne-Guinée, Haute-Guinée and Guinée Forestière – and all prefectures using GN + number codes taken from the national map. If a code or spelling is incorrect, an administrator can amend it here and in the backend.
            </p>
          </div>

          <!-- Interactive map -->
          <div class="mb-8 grid lg:grid-cols-[minmax(0,1.2fr)_minmax(0,1fr)] gap-5">
            <div class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5 space-y-3">
              <h3 class="text-sm font-semibold text-emerald-300" data-i18n="divisions.mapTitle">Interactive Guinea prefecture map</h3>
              <p class="text-xs text-slate-300" data-i18n="divisions.mapSubtitle">Use this Guinea-only map and the prefectures list (GN code, name and administrative region) to see where a land or home record is located. Click a prefecture to center the map and open that location in an online map (for example OpenStreetMap) in a new tab.</p>
              <div class="relative aspect-video w-full rounded-lg overflow-hidden border border-slate-800">
                <iframe
                  id="prefectureMapIframe"
                  src="https://www.google.com/maps?q=Guinea&output=embed"
                  class="w-full h-full border-0"
                  loading="lazy"
                  referrerpolicy="no-referrer-when-downgrade"
                ></iframe>
                <div
                  id="prefectureMapInfo"
                  class="pointer-events-none absolute left-2 right-2 bottom-2 rounded-md bg-slate-950/80 border border-slate-800/80 px-3 py-2 shadow-lg shadow-slate-950/70"
                ></div>
              </div>
            </div>
            <div class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5 space-y-3">
              <h4 class="text-xs font-semibold text-slate-200" data-i18n="divisions.mapListTitle">Prefectures (GN code · name · administrative region)</h4>
              <p class="text-[11px] text-slate-400" data-i18n="divisions.mapListHint">Use this list to verify in which prefecture and region a parcel or home record belongs, then open the location in an online map.</p>
              <div id="prefectureMapList" class="max-h-72 overflow-y-auto space-y-1 text-[11px]"></div>
            </div>
          </div>

          <div id="prefecturesContainer" class="space-y-6"></div>

          <p class="mt-5 text-[11px] text-slate-400" data-i18n="admin.dataDisclaimer">
            Prefecture codes and spellings are based on public sources and may need adjustment. In a real deployment these values live in PostgreSQL (tables <code class="bg-slate-900 px-1 rounded border border-slate-700">regions</code> and <code class="bg-slate-900 px-1 rounded border border-slate-700">prefectures</code>) and can be corrected without code changes.
          </p>
        </div>
      </section>

      <!-- About -->
      <section id="about" class="bg-slate-950">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 py-10 sm:py-14 lg:py-16">
          <div class="grid lg:grid-cols-[minmax(0,1.2fr)_minmax(0,0.9fr)] gap-8 items-start">
            <div>
              <h2 class="text-xl sm:text-2xl font-semibold tracking-tight mb-2" data-i18n="about.sectionTitle">Why Le Record?</h2>
              <p class="text-sm text-slate-300 mb-4" data-i18n="about.footerNote">
                This interface is a conceptual demo for a national land and home registry platform for the Republic of Guinea.
              </p>
              <div class="space-y-3">
                <div class="bg-slate-900/80 border border-slate-800 rounded-xl p-4">
                  <h3 class="text-sm font-semibold text-emerald-300 mb-1" data-i18n="about.bullet1Title">Reliable ownership evidence</h3>
                  <p class="text-xs text-slate-300" data-i18n="about.bullet1Body">
                    Structured, versioned ownership records with full transaction history and links to scanned deeds, survey plans and court orders.
                  </p>
                </div>
                <div class="bg-slate-900/80 border border-slate-800 rounded-xl p-4">
                  <h3 class="text-sm font-semibold text-emerald-300 mb-1" data-i18n="about.bullet2Title">Transparent public access</h3>
                  <p class="text-xs text-slate-300" data-i18n="about.bullet2Body">
                    Anyone can verify a parcel or transaction records for a fee after signing in, while sensitive personal data is protected behind authenticated flows and staff permissions.
                  </p>
                </div>
                <div class="bg-slate-900/80 border border-slate-800 rounded-xl p-4">
                  <h3 class="text-sm font-semibold text-emerald-300 mb-1" data-i18n="about.bullet3Title">Sustainable monetization</h3>
                  <p class="text-xs text-slate-300" data-i18n="about.bullet3Body">
                    Low-cost reports paid via Orange Money, cards, bank transfer or cash finance the maintenance of the national registry and local land offices.
                  </p>
                </div>
              </div>
            </div>

            <div class="space-y-4">
              <div class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5">
                <h3 class="text-sm font-semibold text-slate-200 mb-2" data-i18n="about.demoDisclaimerTitle">Demo data disclaimer</h3>
                <p class="text-xs text-slate-300" data-i18n="about.demoDisclaimerBody">
                  All parcel numbers, owners and transactions in this demo are fictional or approximated for illustration only. They do not represent the real Guinea land registry.
                </p>
                <p class="mt-2 text-[11px] text-slate-400" data-i18n="about.demoDisclaimerBody2">
                  If you notice any incorrect assumption (for example a prefecture name or code), use the admin tools above or inform the technical team so the database can be updated quickly.
                </p>
              </div>
              <div class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5 flex items-center justify-between gap-3">
                <div>
                  <p class="text-xs text-slate-300" data-i18n="about.callToActionTitle">Ready to imagine this in production?</p>
                  <p class="text-[11px] text-slate-500" data-i18n="about.callToActionBody">Create an account, explore the search, then simulate an Orange Money payment flow.</p>
                </div>
                <a href="#accounts" class="inline-flex items-center px-3 py-1.5 rounded-lg bg-emerald-500 text-slate-950 text-xs font-semibold hover:bg-emerald-400 transition" data-i18n="about.callToActionButton">
                  Start demo
                </a>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>

    <!-- Footer -->
    <footer class="border-t border-slate-900 bg-slate-950">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 py-4 flex flex-col sm:flex-row items-center justify-between gap-3 text-[11px] text-slate-500">
        <p>Le Record · Concept demo for the Guinea land &amp; home registry.</p>
        <a href="#hero" class="inline-flex items-center gap-1 text-emerald-300 hover:text-emerald-200" data-i18n="common.backToTop">
          Back to top
        </a>
      </div>
    </footer>
  </div>

  <script>
    (function () {
      const translations = {
        en: {
          brand: {
            name: "Le Record",
            tagline: "Guinea Digital Land & Property Registry"
          },
          nav: {
            home: "Home",
            accounts: "Account & Access",
            search: "Search & Verify",
            reports: "Reports & Pricing",
            developers: "Technical Design",
            divisions: "Regions & Prefectures",
            about: "About",
            login: "Sign in"
          },
          hero: {
            eyebrow: "Republic of Guinea · Ministry of Urban Planning, Housing and Territorial Development",
            title: "One registry for every parcel and home in Guinea’s four natural regions.",
            subtitle: "Le Record, a data company with the sole objectives of searching properties, deeds and transactions records across Basse-Guinée, Moyenne-Guinée, Haute-Guinée and Guinée Forestière, with secure public verification.",
            primaryCta: "Search the registry",
            secondaryCta: "See technical design",
            badgeAccounts: "Users must create an account to search and order official reports.",
            sideTitle: "Registry, billing and payments in one platform",
            sidePoint1: "Land registry core: parcels, owners, ownerships, transactions, disputes and documents modeled in PostgreSQL.",
            sidePoint2: "Monetization: products, orders, payments and signed reports managed by a dedicated billing app.",
            sidePoint3: "Payments: Orange Money as primary mobile money provider, extendable to cards, bank transfer and cash at offices.",
            demoLabel: "Demo only",
            demoBody: "This page is a front-end concept. In production all data and permissions come from a secured Django + PostgreSQL backend operated by the Government of Guinea."
          },
          common: {
            language: "Language",
            english: "English",
            french: "Français",
            status: "Status",
            owner: "Current owner",
            titleNumber: "Title number",
            area: "Area (m²)",
            landUse: "Land use",
            disputes: "Disputes",
            none: "None",
            yes: "Yes",
            no: "No",
            backToTop: "Back to top",
            address: "Address",
            transactionType: "Transaction type",
            parcelNumber: "Parcel number",
            seller: "Seller",
            buyer: "Buyer",
            signedOn: "Signed on",
            registeredOn: "Registered on",
            macroRegion: "Macro-region",
            administrativeRegion: "Administrative region",
            prefecture: "Prefecture",
            prefectureCode: "Prefecture code"
          },
          accounts: {
            sectionTitle: "Create an account to search the registry",
            sectionSubtitle: "For transparency and security, users, professionals and ministries must authenticate and verify their identity before they can search parcels or add property records.",
            signInTab: "Sign in",
            signUpTab: "Create account",
            usernameLabel: "Username",
            passwordLabel: "Password",
            emailLabel: "Email",
            phoneLabel: "Mobile phone",
            userTypeLabel: "Account type",
            organizationLabel: "Organization / ministry (if applicable)",
            userTypeIndividual: "Individual user",
            userTypeProfessional: "Professional (notary, surveyor, banker…)",
            userTypeInstitution: "Institution / company",
            userTypeStaff: "Government staff",
            ministryWorkerLabel: "I work for a ministry or public agency",
            verifyByLabel: "Choose how to verify your account:",
            verifyByEmail: "Email link",
            verifyBySms: "SMS code",
            humanCheckLabel: "I confirm that I am a human user and not an automated bot.",
            signInButton: "Sign in",
            signUpButton: "Create account",
            signOutButton: "Sign out",
            signedInAs: "Signed in",
            notSignedIn: "Not signed in. Use the forms below to access the registry.",
            noUserYet: "No account yet? Create one below.",
            demoAdminHint: "Demo: sign in with username \"admin\" and password \"admin\" to manage ministry permissions.",
            invalidCredentials: "Username or password is incorrect.",
            usernameRequired: "Choose a username to create an account.",
            passwordRequired: "Choose a password to create an account.",
            emailRequired: "Enter an email address to create an account.",
            phoneRequired: "Enter a mobile phone number starting with +224 to create an account.",
            humanCheckRequired: "Please confirm that you are a human user (not a bot).",
            usernameTaken: "This username is already used. Pick another one.",
            simulateVerifyButton: "Mark account as verified (demo)"
          },
          search: {
            sectionTitle: "Public search & verification",
            sectionDesc: "After signing in, look up parcels and transactions to verify land information before buying, selling or requesting official reports.",
            parcelTab: "Parcel",
            transactionTab: "Transaction",
            parcelPlaceholder: "Example: GN-4-2023-000001",
            transactionPlaceholder: "Example: TXN-2023-000045",
            searchButton: "Search",
            parcelResultTitle: "Parcel",
            transactionResultTitle: "Transaction",
            notFoundTitle: "No results",
            notFoundBody: "We could not find a record matching the number you entered. Check the format or contact the registry office.",
            hasActiveDispute: "Active dispute",
            viewOrderOptions: "Order an official report",
            loginRequiredTitle: "Account required",
            loginRequiredBody: "Create an account or sign in to use the public registry search in this demo.",
            loginRequiredCta: "Go to account section",
            demoNotice: "Mock data only – no real parcels or owners are loaded.",
            journeyTitle: "3-step user journey",
            journeyStep1: "Create an account and pay to search the parcel or transaction.",
            journeyStep2: "Confirm that the information matches paper records and local knowledge.",
            journeyStep3: "Order a certified report when you need legal proof.",
            privacyNote: "No personal owner identifiers (ID numbers, full private addresses) are exposed in public search.",
            guineaTitle: "Guinea-focused design",
            guineaPoint1: "• Four natural regions (Basse, Moyenne, Haute, Forestière) and all prefectures encoded with GN + number codes.",
            guineaPoint2: "• Orange Money as the primary payment channel, extendable to cards, bank transfer and cash.",
            guineaPoint3: "• Compatible with cash offices, offline workflows and paper archives."
          },
          reports: {
            sectionTitle: "Monetized reports & extracts",
            sectionDesc: "Le Record monetizes access to parcel and home records: users pay to research a property or land records for informational or transactional reasons.",
            chooseProduct: "Choose a product",
            fullReport: "Full Property Report",
            fullReportDesc: "Complete history of the parcel, owners, transactions and linked documents.",
            certExtract: "Certified Extract",
            certExtractDesc: "Legally certified extract for notaries, banks and courts.",
            price: "Price",
            simulateOrder: "Create demo order",
            orderSummaryTitle: "Order summary",
            orderSummaryHint: "Uses mock data mapped to the real Django models.",
            parcelNumberLabel: "Parcel number",
            transactionNumberLabel: "Transaction number",
            amountLabel: "Total amount",
            statusLabel: "Order status",
            payWithOrangeMoney: "Pay with Orange Money (demo)",
            phoneLabel: "Orange Money phone number",
            startPayment: "Start payment",
            paymentTimelineTitle: "Payment simulation",
            timelineCreated: "Order created (PENDING)",
            timelineInit: "Payment initiated with Orange Money",
            timelineWebhook: "Webhook received · payment SUCCESS",
            timelineReport: "Report generated and attached to order",
            downloadSampleReport: "Open sample report",
            paymentSuccessNote: "In production, status is driven entirely by real-time callbacks from Orange Money and the banking gateway.",
            qrCodeTitle: "Verification QR code (demo)",
            qrCodeHint: "In production, scanning this QR code would open an online verification page for this exact parcel or transaction report.",
            noOrderYetTitle: "No order yet",
            noOrderYetBody: "Search for a parcel or transaction, select a product, then click \"Create demo order\".",
            noOrderForPayment: "Create a demo order first, then start the payment.",
            phoneRequired: "Enter an Orange Money phone number starting with +224 to simulate a payment.",
            authRequiredForOrder: "You must be signed in to create a demo order."
          },
          dev: {
            sectionTitle: "Technical architecture",
            stackTitle: "Core stack",
            stackBody: "Le Record is designed around a robust Django + PostgreSQL backend with a modern API layer, custom accounts, Orange Money integration and data-driven regions and prefectures.",
            stackPoint1: "• Django + Django REST Framework with a custom Account user model (users, professionals, institutions, staff).",
            stackPoint2: "• PostgreSQL schema for regions, prefectures, communes, parcels, owners, ownerships, transactions, disputes and documents.",
            stackPoint3: "• Separate billing app for products, orders, payments and generated reports.",
            dbTitle: "Registry data model (simplified)",
            dbBody: "Administrative tables store the four natural regions and all prefectures with GN + number codes. Core land tables store parcels, owners, ownership records, transactions, disputes and supporting documents.",
            dbPoint1: "• ownerships table tracks current and historical rights per parcel.",
            dbPoint2: "• transactions store prices, fees, taxes and registrar decisions.",
            dbPoint3: "• disputes flag conflicted parcels and drive public status.",
            apiTitle: "Public APIs",
            apiBody: "A Django REST Framework public app exposes read-only APIs for parcel and transaction lookup, plus authenticated endpoints for ordering reports and initiating Orange Money payments.",
            endpointsTitle: "Key endpoints (illustrative)",
            endpointParcel: "GET /api/public/parcels/{parcel_number}/",
            endpointParcelDesc: "Parcel lookup + current owner, title and prefecture snapshot.",
            endpointTransaction: "GET /api/public/transactions/{transaction_number}/",
            endpointTransactionDesc: "Transaction type, parties, status and linked parcel.",
            endpointOrder: "POST /api/billing/orders/parcel-report/",
            endpointOrderDesc: "Authenticated creation of a paid order for a parcel or transaction.",
            endpointPay: "POST /api/billing/orders/{order_id}/pay/",
            endpointPayDesc: "Initiate Orange Money or other payments.",
            omTitle: "Orange Money integration",
            omBody: "A dedicated payment provider handles Orange Money flows: initiating payments, handling asynchronous webhooks and updating Order and Payment records atomically.",
            omStep1: "User or institution creates an Order for a product (e.g. FULL_REPORT).",
            omStep2: "The backend creates a Payment row and calls the Orange Money API via OrangeMoneyProvider.",
            omStep3: "Orange Money redirects or pushes an STK request to the user’s wallet.",
            omStep4: "The asynchronous webhook updates Payment.status and Order.status atomically.",
            omStep5: "A background task generates a signed PDF Report and stores its URL.",
            securityTitle: "Security & governance",
            securityBody: "Role-based access, ministry-level permissions, verified staff accounts, signed reports and immutable transaction logs ensure legal-grade evidence for ownership changes. The registry super-administrator is the onboarding point for all ministries and staff who can create or update land, property and transaction records.",
            securityPoint1: "• Staff users (registrars, surveyors) onboarded as Account with STAFF type.",
            securityPoint2: "• Ministries and agencies grouped with explicit ‘can_add_property_records’ permissions.",
            securityPoint3: "• Every change to parcels, ownerships or disputes is versioned and auditable.",
            securityPoint4: "• Reports are signed with digital seals, include a 'Le Record – Ministère de l’Urbanisme, de l’Habitat et de l’Aménagement du territoire' watermark, and have verifiable QR codes."
          },
          divisions: {
            sectionTitle: "Regions & prefectures of Guinea",
            sectionDesc: "This demo models Guinea with four natural regions – Basse-Guinée, Moyenne-Guinée, Haute-Guinée and Guinée Forestière – and all prefectures using GN + number codes taken from the national map. If a code or spelling is incorrect, an administrator can amend it here and in the backend.",
            macroRegionIntro: "The four natural regions group the administrative regions and prefectures:",
            macroBG: "Basse-Guinée: coastal belt including Boké, Kindia and Conakry regions.",
            macroMG: "Moyenne-Guinée: Fouta Djallon highlands around Labé and Mamou.",
            macroHG: "Haute-Guinée: interior plateau around Faranah and Kankan.",
            macroFG: "Guinée Forestière: forest region around Nzérékoré.",
            prefectureTableTitle: "Prefectures and GN codes",
            mapTitle: "Interactive Guinea prefecture map",
            mapSubtitle: "Use this Guinea-only map and the prefectures list (GN code, name and administrative region) to see where a land or home record is located. Click a prefecture to center the map and open that location in an online map (for example OpenStreetMap) in a new tab.",
            mapListTitle: "Prefectures (GN code · name · administrative region)",
            mapListHint: "Use this list to verify in which prefecture and region a parcel or home record belongs, then open the location in an online map.",
            mapInfoPlaceholder: "Click a prefecture in the list to see its code, name and administrative region here while keeping the map focused on Guinea."
          },
          admin: {
            ministriesTitle: "Ministries & agencies with registry access",
            ministriesIntro: "In production, only the registry super-administrator and explicitly authorized ministries and agencies can onboard and update land, property and transaction records in Le Record. This demo lets an administrator simulate which ministries are allowed to add parcels and transactions.",
            canCreateParcels: "May create and update property records",
            yesShort: "Yes",
            noShort: "No",
            toggleGrant: "Grant permission",
            toggleRevoke: "Revoke permission",
            adminOnlyNote: "You are signed in as an administrator. Changes you make here simulate ministry-level permissions.",
            notAdminNote: "You are signed in as a regular user. Permissions below are read-only in this demo.",
            editPrefectureButton: "Edit name/code",
            editPrefecturePromptName: "Update the display name for this prefecture:",
            editPrefecturePromptCode: "Update the public code for this prefecture (for example: GN4):",
            dataDisclaimer: "Prefecture codes and spellings are based on public sources and may need adjustment. In a real deployment these values live in PostgreSQL (tables ‘regions’ and ‘prefectures’) and can be corrected without code changes."
          },
          about: {
            sectionTitle: "Why Le Record?",
            bullet1Title: "Reliable ownership evidence",
            bullet1Body: "Structured, versioned ownership records with full transaction history and links to scanned deeds, survey plans and court orders.",
            bullet2Title: "Transparent public access",
            bullet2Body: "Anyone can verify a parcel or transaction records for a fee after signing in, while sensitive personal data is protected behind authenticated flows and staff permissions.",
            bullet3Title: "Sustainable monetization",
            bullet3Body: "Low-cost reports paid via Orange Money, cards, bank transfer or cash finance the maintenance of the national registry and local land offices.",
            footerNote: "This interface is a conceptual demo for a national land and home registry platform for the Republic of Guinea.",
            demoDisclaimerTitle: "Demo data disclaimer",
            demoDisclaimerBody: "All parcel numbers, owners and transactions in this demo are fictional or approximated for illustration only. They do not represent the real Guinea land registry.",
            demoDisclaimerBody2: "If you notice any incorrect assumption (for example a prefecture name or code), use the admin tools above or inform the technical team so the database can be updated quickly.",
            callToActionTitle: "Ready to imagine this in production?",
            callToActionBody: "Create an account, explore the search, then simulate an Orange Money payment flow.",
            callToActionButton: "Start demo"
          },
          statuses: {
            PENDING: "Pending",
            REGISTERED: "Registered",
            DISPUTED: "Disputed",
            CANCELLED: "Cancelled",
            SUBMITTED: "Submitted",
            UNDER_REVIEW: "Under review",
            REJECTED: "Rejected"
          },
          txnTypes: {
            SALE: "Sale",
            GIFT: "Gift",
            INHERITANCE: "Inheritance",
            EXPROPRIATION: "Expropriation",
            MORTGAGE: "Mortgage",
            RELEASE: "Mortgage release",
            OTHER: "Other"
          },
          orderStatus: {
            PENDING: "Pending",
            PAID: "Paid",
            FAILED: "Failed",
            CANCELLED: "Cancelled"
          },
          paymentStatus: {
            PENDING: "Pending",
            SUCCESS: "Success",
            FAILED: "Failed"
          }
        },
        fr: {
          brand: {
            name: "Le Record",
            tagline: "Registre Numérique Foncier & Immobilier de Guinée"
          },
          nav: {
            home: "Accueil",
            accounts: "Compte & Accès",
            search: "Recherche & Vérification",
            reports: "Rapports & Tarifs",
            developers: "Architecture Technique",
            divisions: "Régions & Préfectures",
            about: "À propos",
            login: "Connexion"
          },
          hero: {
            eyebrow: "République de Guinée · Ministère de l’Urbanisme, de l’Habitat et de l’Aménagement du territoire",
            title: "Un registre unique pour chaque parcelle et logement des quatre régions naturelles de Guinée.",
            subtitle: "Le Record, une société de données dont l’unique objectif est la recherche de biens, d’actes et de dossiers de transactions à travers la Basse-Guinée, la Moyenne-Guinée, la Haute-Guinée et la Guinée Forestière, avec vérification publique sécurisée.",
            primaryCta: "Rechercher dans le registre",
            secondaryCta: "Voir l’architecture technique",
            badgeAccounts: "Les utilisateurs doivent créer un compte pour rechercher et commander des rapports officiels.",
            sideTitle: "Registre, facturation et paiements dans une seule plateforme",
            sidePoint1: "Noyau foncier : parcelles, propriétaires, droits, transactions, litiges et documents modélisés dans PostgreSQL.",
            sidePoint2: "Monétisation : produits, commandes, paiements et rapports signés gérés par une application de facturation dédiée.",
            sidePoint3: "Paiements : Orange Money comme principal moyen de mobile money, extensible aux cartes, virements bancaires et paiements en espèces.",
            demoLabel: "Démo uniquement",
            demoBody: "Cette page est un concept d’interface. En production, toutes les données et autorisations proviennent d’un backend Django + PostgreSQL sécurisé et opéré par l’État guinéen."
          },
          common: {
            language: "Langue",
            english: "English",
            french: "Français",
            status: "Statut",
            owner: "Propriétaire actuel",
            titleNumber: "Numéro de titre",
            area: "Superficie (m²)",
            landUse: "Affectation du sol",
            disputes: "Litiges",
            none: "Aucun",
            yes: "Oui",
            no: "Non",
            backToTop: "Retour en haut",
            address: "Adresse",
            transactionType: "Type de transaction",
            parcelNumber: "Numéro de parcelle",
            seller: "Vendeur",
            buyer: "Acheteur",
            signedOn: "Signé le",
            registeredOn: "Enregistré le",
            macroRegion: "Région naturelle",
            administrativeRegion: "Région administrative",
            prefecture: "Préfecture",
            prefectureCode: "Code de préfecture"
          },
          accounts: {
            sectionTitle: "Créer un compte pour rechercher dans le registre",
            sectionSubtitle: "Pour la transparence et la sécurité, utilisateurs, professionnels et ministères doivent s’authentifier et vérifier leur identité avant de rechercher des parcelles ou d’ajouter des dossiers fonciers.",
            signInTab: "Connexion",
            signUpTab: "Créer un compte",
            usernameLabel: "Nom d’utilisateur",
            passwordLabel: "Mot de passe",
            emailLabel: "Email",
            phoneLabel: "Téléphone mobile",
            userTypeLabel: "Type de compte",
            organizationLabel: "Organisation / ministère (le cas échéant)",
            userTypeIndividual: "Utilisateur individuel",
            userTypeProfessional: "Professionnel (notaire, géomètre, banquier…)",
            userTypeInstitution: "Institution / entreprise",
            userTypeStaff: "Agent de l’État",
            ministryWorkerLabel: "Je travaille pour un ministère ou un organisme public",
            verifyByLabel: "Choisissez le mode de vérification de votre compte :",
            verifyByEmail: "Lien email",
            verifyBySms: "Code SMS",
            humanCheckLabel: "Je confirme que je suis un utilisateur humain et non un robot.",
            signInButton: "Se connecter",
            signUpButton: "Créer le compte",
            signOutButton: "Se déconnecter",
            signedInAs: "Connecté",
            notSignedIn: "Non connecté. Utilisez les formulaires ci-dessous pour accéder au registre.",
            noUserYet: "Pas encore de compte ? Créez-en un ci-dessous.",
            demoAdminHint: "Démo : connectez-vous avec l’identifiant \"admin\" et le mot de passe \"admin\" pour gérer les autorisations des ministères.",
            invalidCredentials: "Nom d’utilisateur ou mot de passe incorrect.",
            usernameRequired: "Choisissez un nom d’utilisateur pour créer un compte.",
            passwordRequired: "Choisissez un mot de passe pour créer un compte.",
            emailRequired: "Renseignez une adresse email pour créer un compte.",
            phoneRequired: "Renseignez un numéro de téléphone mobile commençant par +224 pour créer un compte.",
            humanCheckRequired: "Veuillez confirmer que vous êtes un utilisateur humain (et non un robot).",
            usernameTaken: "Ce nom d’utilisateur est déjà utilisé. Veuillez en choisir un autre.",
            simulateVerifyButton: "Marquer le compte comme vérifié (démo)"
          },
          search: {
            sectionTitle: "Recherche publique & vérification",
            sectionDesc: "Après connexion, consultez les parcelles et les transactions pour vérifier les informations foncières avant tout achat, vente ou demande d’extrait officiel.",
            parcelTab: "Parcelle",
            transactionTab: "Transaction",
            parcelPlaceholder: "Exemple : GN-4-2023-000001",
            transactionPlaceholder: "Exemple : TXN-2023-000045",
            searchButton: "Rechercher",
            parcelResultTitle: "Parcelle",
            transactionResultTitle: "Transaction",
            notFoundTitle: "Aucun résultat",
            notFoundBody: "Aucun enregistrement ne correspond au numéro saisi. Vérifiez le format ou contactez le service du cadastre.",
            hasActiveDispute: "Litige actif",
            viewOrderOptions: "Commander un rapport officiel",
            loginRequiredTitle: "Compte requis",
            loginRequiredBody: "Créez un compte ou connectez-vous pour utiliser la recherche publique dans cette démo.",
            loginRequiredCta: "Aller à la section Compte",
            demoNotice: "Données simulées uniquement – aucune parcelle ou propriétaire réel n’est chargé.",
            journeyTitle: "Parcours utilisateur en 3 étapes",
            journeyStep1: "Créer un compte et payer pour rechercher la parcelle ou la transaction.",
            journeyStep2: "Vérifier que les informations correspondent aux dossiers papier et à la connaissance locale.",
            journeyStep3: "Commander un rapport certifié lorsque vous avez besoin d’une preuve légale.",
            privacyNote: "Aucun identifiant personnel (numéros d’ID, adresses privées complètes) n’est exposé dans la recherche publique.",
            guineaTitle: "Conçu pour la Guinée",
            guineaPoint1: "• Quatre régions naturelles (Basse, Moyenne, Haute, Forestière) et toutes les préfectures codées GN + numéro.",
            guineaPoint2: "• Orange Money comme canal de paiement principal, extensible aux cartes, virements et espèces.",
            guineaPoint3: "• Compatible avec les guichets physiques, les flux hors ligne et les archives papier."
          },
          reports: {
            sectionTitle: "Rapports monétisés & extraits",
            sectionDesc: "Le Record monétise l’accès aux informations foncières et immobilières : les utilisateurs paient pour rechercher une parcelle ou des dossiers fonciers à des fins informationnelles ou transactionnelles.",
            chooseProduct: "Choisir un produit",
            fullReport: "Rapport complet de propriété",
            fullReportDesc: "Historique complet de la parcelle, des propriétaires, des transactions et des documents liés.",
            certExtract: "Extrait certifié",
            certExtractDesc: "Extrait légalement certifié pour notaires, banques et tribunaux.",
            price: "Prix",
            simulateOrder: "Créer une commande de démonstration",
            orderSummaryTitle: "Récapitulatif de la commande",
            orderSummaryHint: "Utilise des données fictives alignées sur les modèles Django réels.",
            parcelNumberLabel: "Numéro de parcelle",
            transactionNumberLabel: "Numéro de transaction",
            amountLabel: "Montant total",
            statusLabel: "Statut de la commande",
            payWithOrangeMoney: "Payer avec Orange Money (démo)",
            phoneLabel: "Numéro Orange Money",
            startPayment: "Lancer le paiement",
            paymentTimelineTitle: "Simulation du paiement",
            timelineCreated: "Commande créée (PENDING)",
            timelineInit: "Paiement initié auprès d’Orange Money",
            timelineWebhook: "Webhook reçu · paiement SUCCESS",
            timelineReport: "Rapport généré et rattaché à la commande",
            downloadSampleReport: "Ouvrir un rapport d’exemple",
            paymentSuccessNote: "En production, le statut est piloté uniquement par les callbacks temps réel d’Orange Money et de la passerelle bancaire.",
            qrCodeTitle: "QR code de vérification (démo)",
            qrCodeHint: "En production, le scan de ce QR code ouvrirait une page de vérification en ligne pour ce rapport précis de parcelle ou de transaction.",
            noOrderYetTitle: "Aucune commande",
            noOrderYetBody: "Recherchez une parcelle ou une transaction, sélectionnez un produit puis cliquez sur « Créer une commande de démonstration ».",
            noOrderForPayment: "Créez d’abord une commande de démonstration, puis lancez le paiement.",
            phoneRequired: "Saisissez un numéro Orange Money commençant par +224 pour simuler un paiement.",
            authRequiredForOrder: "Vous devez être connecté pour créer une commande de démonstration."
          },
          dev: {
            sectionTitle: "Architecture technique",
            stackTitle: "Piliers technologiques",
            stackBody: "Le Record s’appuie sur un backend robuste Django + PostgreSQL avec une couche d’API moderne, des comptes personnalisés, l’intégration Orange Money et des régions/préfectures pilotées par les données.",
            stackPoint1: "• Django + Django REST Framework avec un modèle utilisateur Account personnalisé (utilisateurs, professionnels, institutions, agents).",
            stackPoint2: "• Schéma PostgreSQL pour régions, préfectures, communes, parcelles, propriétaires, droits, transactions, litiges et documents.",
            stackPoint3: "• Application de facturation séparée pour les produits, commandes, paiements et rapports générés.",
            dbTitle: "Modèle de données du registre (simplifié)",
            dbBody: "Les tables administratives stockent les quatre régions naturelles et toutes les préfectures avec codes GN + numéro. Les tables foncières stockent les parcelles, propriétaires, droits, transactions, litiges et documents justificatifs.",
            dbPoint1: "• La table ownerships suit les droits actuels et historiques par parcelle.",
            dbPoint2: "• Les transactions stockent prix, frais, taxes et décisions du conservateur.",
            dbPoint3: "• Les litiges (disputes) signalent les parcelles en conflit et pilotent le statut public.",
            apiTitle: "APIs publiques",
            apiBody: "Une application publique Django REST Framework expose des APIs en lecture seule pour la recherche de parcelles et de transactions, ainsi que des endpoints authentifiés pour commander des rapports et initier des paiements Orange Money.",
            endpointsTitle: "Endpoints clés (illustration)",
            endpointParcel: "GET /api/public/parcels/{parcel_number}/",
            endpointParcelDesc: "Recherche d’une parcelle + propriétaire, titre et préfecture actuels.",
            endpointTransaction: "GET /api/public/transactions/{transaction_number}/",
            endpointTransactionDesc: "Type de transaction, parties, statut et parcelle liée.",
            endpointOrder: "POST /api/billing/orders/parcel-report/",
            endpointOrderDesc: "Création authentifiée d’une commande payante pour une parcelle ou une transaction.",
            endpointPay: "POST /api/billing/orders/{order_id}/pay/",
            endpointPayDesc: "Initiation des paiements Orange Money ou autres.",
            omTitle: "Intégration Orange Money",
            omBody: "Un fournisseur de paiement dédié gère les flux Orange Money : initiation du paiement, gestion des webhooks asynchrones et mise à jour atomique des enregistrements Order et Payment.",
            omStep1: "L’utilisateur ou l’institution crée une commande (Order) pour un produit (ex : FULL_REPORT).",
            omStep2: "Le backend crée un paiement (Payment) et appelle l’API Orange Money via OrangeMoneyProvider.",
            omStep3: "Orange Money redirige l’utilisateur ou envoie une demande STK sur son portefeuille.",
            omStep4: "Le webhook asynchrone met à jour les statuts Payment.status et Order.status de manière atomique.",
            omStep5: "Une tâche de fond génère un rapport PDF signé et en stocke l’URL.",
            securityTitle: "Sécurité & gouvernance",
            securityBody: "Des rôles clairs, des autorisations au niveau des ministères, des comptes agents vérifiés, des rapports signés et des journaux d’audit immuables garantissent une preuve juridique des changements de propriété. L’administrateur du registre est le point d’entrée pour l’intégration des ministères et des agents habilités à créer ou mettre à jour des dossiers fonciers, immobiliers et de transactions.",
            securityPoint1: "• Les agents (conservateurs, géomètres) sont intégrés comme Account avec type STAFF.",
            securityPoint2: "• Les ministères et organismes sont regroupés avec des permissions explicites ‘can_add_property_records’.",
            securityPoint3: "• Chaque modification des parcelles, droits ou litiges est versionnée et traçable.",
            securityPoint4: "• Les rapports sont signés avec des sceaux numériques, comportent un filigrane « Le Record – Ministère de l’Urbanisme, de l’Habitat et de l’Aménagement du territoire » et des QR codes vérifiables."
          },
          divisions: {
            sectionTitle: "Régions & préfectures de Guinée",
            sectionDesc: "Cette démo modélise la Guinée avec quatre régions naturelles – Basse-Guinée, Moyenne-Guinée, Haute-Guinée et Guinée Forestière – et toutes les préfectures utilisant des codes GN + numéro issus de la carte nationale. Si un code ou une orthographe est incorrect, un administrateur peut le corriger ici et dans le backend.",
            macroRegionIntro: "Les quatre régions naturelles regroupent les régions administratives et les préfectures :",
            macroBG: "Basse-Guinée : bande côtière incluant les régions de Boké, Kindia et Conakry.",
            macroMG: "Moyenne-Guinée : massif du Fouta-Djalon autour de Labé et Mamou.",
            macroHG: "Haute-Guinée : plateau intérieur autour de Faranah et Kankan.",
            macroFG: "Guinée Forestière : région forestière autour de Nzérékoré.",
            prefectureTableTitle: "Préfectures et codes GN",
            mapTitle: "Carte interactive des préfectures de Guinée",
            mapSubtitle: "Utilisez cette carte centrée sur la Guinée et la liste des préfectures (code GN, nom et région administrative) pour localiser un dossier foncier ou immobilier. Cliquez sur une préfecture pour centrer la carte et ouvrir ce lieu dans une carte en ligne (par exemple OpenStreetMap) dans un nouvel onglet.",
            mapListTitle: "Préfectures (code GN · nom · région administrative)",
            mapListHint: "Servez-vous de cette liste pour vérifier dans quelle préfecture et région se trouve une parcelle ou un logement, puis ouvrez l’emplacement dans une carte en ligne.",
            mapInfoPlaceholder: "Cliquez sur une préfecture dans la liste pour voir ici son code, son nom et sa région administrative tout en gardant la carte centrée sur la Guinée."
          },
          admin: {
            ministriesTitle: "Ministères & organismes avec accès au registre",
            ministriesIntro: "En production, seuls l’administrateur du registre et les ministères/organismes explicitement autorisés peuvent intégrer et mettre à jour des dossiers fonciers, immobiliers et de transactions dans Le Record. Cette démo permet à un administrateur de simuler quels ministères peuvent créer des parcelles et des transactions.",
            canCreateParcels: "Peut créer et mettre à jour des dossiers fonciers",
            yesShort: "Oui",
            noShort: "Non",
            toggleGrant: "Accorder l’autorisation",
            toggleRevoke: "Retirer l’autorisation",
            adminOnlyNote: "Vous êtes connecté en tant qu’administrateur. Les changements effectués ici simulent des permissions au niveau des ministères.",
            notAdminNote: "Vous êtes connecté en tant qu’utilisateur standard. Les autorisations ci-dessous sont en lecture seule dans cette démo.",
            editPrefectureButton: "Modifier nom/code",
            editPrefecturePromptName: "Mettre à jour le nom d’affichage de cette préfecture :",
            editPrefecturePromptCode: "Mettre à jour le code public de cette préfecture (par exemple : GN4) :",
            dataDisclaimer: "Les codes et orthographes des préfectures sont basés sur des sources publiques et peuvent nécessiter des ajustements. En production, ces valeurs sont stockées dans PostgreSQL (tables ‘regions’ et ‘prefectures’) et peuvent être corrigées sans changement de code."
          },
          about: {
            sectionTitle: "Pourquoi Le Record ?",
            bullet1Title: "Preuve de propriété fiable",
            bullet1Body: "Enregistrements de propriété structurés et versionnés, avec historique complet des transactions et liens vers les actes scannés, plans et décisions de justice.",
            bullet2Title: "Accès public transparent",
            bullet2Body: "Tout utilisateur peut vérifier une parcelle ou une transaction moyennant des frais après connexion, tandis que les données personnelles sensibles restent protégées derrière des parcours authentifiés et des permissions agents.",
            bullet3Title: "Monétisation durable",
            bullet3Body: "Des rapports à faible coût, payés via Orange Money, carte, virement ou espèces, financent la maintenance du registre national et des services fonciers locaux.",
            footerNote: "Cette interface est une démo conceptuelle pour une plateforme nationale de registre foncier et immobilier de la République de Guinée.",
            demoDisclaimerTitle: "Avertissement sur les données de déмо",
            demoDisclaimerBody: "Tous les numéros de parcelle, propriétaires et transactions de cette démo sont fictifs ou approximatifs à des fins d’illustration. Ils ne représentent pas le registre foncier réel de Guinée.",
            demoDisclaimerBody2: "Si vous constatez une hypothèse incorrecte (par exemple un nom ou un code de préfecture), utilisez les outils d’admin ci-dessus ou informez l’équipe technique afin que la base de données soit mise à jour rapidement.",
            callToActionTitle: "Prêt à imaginer cela en production ?",
            callToActionBody: "Créez un compte, explorez la recherche puis simulez un flux de paiement Orange Money.",
            callToActionButton: "Lancer la démo"
          },
          statuses: {
            PENDING: "En attente",
            REGISTERED: "Enregistré",
            DISPUTED: "En litige",
            CANCELLED: "Annulé",
            SUBMITTED: "Soumis",
            UNDER_REVIEW: "En cours d’examen",
            REJECTED: "Rejeté"
          },
          txnTypes: {
            SALE: "Vente",
            GIFT: "Donation",
            INHERITANCE: "Héritage",
            EXPROPRIATION: "Expropriation",
            MORTGAGE: "Hypothèque",
            RELEASE: "Mainlevée d’hypothèque",
            OTHER: "Autre"
          },
          orderStatus: {
            PENDING: "En attente",
            PAID: "Payée",
            FAILED: "Échouée",
            CANCELLED: "Annulée"
          },
          paymentStatus: {
            PENDING: "En attente",
            SUCCESS: "Réussie",
            FAILED: "Échouée"
          }
        }
      };

      // Macro-regions (4 natural regions of Guinea)
      const macroRegions = [
        {
          key: "BASSE",
          name_en: "Basse-Guinée (Lower Guinea)",
          name_fr: "Basse-Guinée"
        },
        {
          key: "MOYENNE",
          name_en: "Moyenne-Guinée (Middle Guinea)",
          name_fr: "Moyenne-Guinée"
        },
        {
          key: "HAUTE",
          name_en: "Haute-Guinée (Upper Guinea)",
          name_fr: "Haute-Guinée"
        },
        {
          key: "FORESTIERE",
          name_en: "Guinée Forestière (Forest Guinea)",
          name_fr: "Guinée Forestière"
        }
      ];

      // Default prefectures with GN + number codes (from provided list)
      const defaultPrefectures = [
        // Boké region (Basse-Guinée)
        { id: 2, code: "GN2", name: "Boffa", administrative_region: "Boké", macro_region_key: "BASSE" },
        { id: 3, code: "GN3", name: "Boké", administrative_region: "Boké", macro_region_key: "BASSE" },
        { id: 12, code: "GN12", name: "Fria", administrative_region: "Boké", macro_region_key: "BASSE" },
        { id: 13, code: "GN13", name: "Gaoual", administrative_region: "Boké", macro_region_key: "BASSE" },
        { id: 20, code: "GN20", name: "Koundara", administrative_region: "Boké", macro_region_key: "BASSE" },
        // Conakry (Basse-Guinée)
        { id: 4, code: "GN4", name: "Conakry", administrative_region: "Conakry", macro_region_key: "BASSE" },
        // Faranah region (Haute-Guinée)
        { id: 6, code: "GN6", name: "Dabola", administrative_region: "Faranah", macro_region_key: "HAUTE" },
        { id: 8, code: "GN8", name: "Dinguiraye", administrative_region: "Faranah", macro_region_key: "HAUTE" },
        { id: 10, code: "GN10", name: "Faranah", administrative_region: "Faranah", macro_region_key: "HAUTE" },
        { id: 18, code: "GN18", name: "Kissidougou", administrative_region: "Faranah", macro_region_key: "HAUTE" },
        // Kankan region (Haute-Guinée)
        { id: 15, code: "GN15", name: "Kankan", administrative_region: "Kankan", macro_region_key: "HAUTE" },
        { id: 16, code: "GN16", name: "Kérouané", administrative_region: "Kankan", macro_region_key: "HAUTE" },
        { id: 21, code: "GN21", name: "Kouroussa", administrative_region: "Kankan", macro_region_key: "HAUTE" },
        { id: 28, code: "GN28", name: "Mandiana", administrative_region: "Kankan", macro_region_key: "HAUTE" },
        { id: 31, code: "GN31", name: "Siguiri", administrative_region: "Kankan", macro_region_key: "HAUTE" },
        // Kindia region (Basse-Guinée)
        { id: 5, code: "GN5", name: "Coyah", administrative_region: "Kindia", macro_region_key: "BASSE" },
        { id: 9, code: "GN9", name: "Dubréka", administrative_region: "Kindia", macro_region_key: "BASSE" },
        { id: 11, code: "GN11", name: "Forécariah", administrative_region: "Kindia", macro_region_key: "BASSE" },
        { id: 17, code: "GN17", name: "Kindia", administrative_region: "Kindia", macro_region_key: "BASSE" },
        { id: 32, code: "GN32", name: "Télimélé", administrative_region: "Kindia", macro_region_key: "BASSE" },
        // Labé region (Moyenne-Guinée)
        { id: 19, code: "GN19", name: "Koubia", administrative_region: "Labé", macro_region_key: "MOYENNE" },
        { id: 22, code: "GN22", name: "Labé", administrative_region: "Labé", macro_region_key: "MOYENNE" },
        { id: 23, code: "GN23", name: "Lélouma", administrative_region: "Labé", macro_region_key: "MOYENNE" },
        { id: 26, code: "GN26", name: "Mali", administrative_region: "Labé", macro_region_key: "MOYENNE" },
        { id: 33, code: "GN33", name: "Tougué", administrative_region: "Labé", macro_region_key: "MOYENNE" },
        // Mamou region (Moyenne-Guinée)
        { id: 7, code: "GN7", name: "Dalaba", administrative_region: "Mamou", macro_region_key: "MOYENNE" },
        { id: 27, code: "GN27", name: "Mamou", administrative_region: "Mamou", macro_region_key: "MOYENNE" },
        { id: 30, code: "GN30", name: "Pita", administrative_region: "Mamou", macro_region_key: "MOYENNE" },
        // Nzérékoré region (Guinée Forestière)
        { id: 1, code: "GN1", name: "Beyla", administrative_region: "Nzérékoré", macro_region_key: "FORESTIERE" },
        { id: 14, code: "GN14", name: "Guéckédou", administrative_region: "Nzérékoré", macro_region_key: "FORESTIERE" },
        { id: 24, code: "GN24", name: "Lola", administrative_region: "Nzérékoré", macro_region_key: "FORESTIERE" },
        { id: 25, code: "GN25", name: "Macenta", administrative_region: "Nzérékoré", macro_region_key: "FORESTIERE" },
        { id: 29, code: "GN29", name: "Nzérékoré", administrative_region: "Nzérékoré", macro_region_key: "FORESTIERE" },
        { id: 34, code: "GN34", name: "Yomou", administrative_region: "Nzérékoré", macro_region_key: "FORESTIERE" }
      ];

      // Default ministries / agencies with permissions
      const defaultMinistries = [
        {
          id: "MHUD",
          name_en: "Ministry of Urban Planning, Housing and Territorial Development",
          name_fr: "Ministère de l’Urbanisme, de l’Habitat et de l’Aménagement du Territoire",
          can_add_parcels: true
        },
        {
          id: "MDAT",
          name_en: "Ministry of Decentralization and Territorial Administration",
          name_fr: "Ministère de la Décentralisation et de l’Administration du Territoire",
          can_add_parcels: true
        },
        {
          id: "DNDC",
          name_en: "National Directorate of Lands and Cadastre (example)",
          name_fr: "Direction Nationale des Domaines et du Cadastre (exemple)",
          can_add_parcels: true
        }
      ];

      // Sample parcels and transactions (mock data)
      const sampleParcels = [
        {
          parcel_number: "GN-4-2023-000001",
          address_text: "Kaloum, Conakry, Guinea",
          area_m2: 450.75,
          land_use: "Residential",
          status: "REGISTERED",
          has_active_dispute: false,
          current_owner: "Société Immobilière de Guinée",
          current_title_number: "TIT-2023-000045",
          prefecture_code: "GN4"
        },
        {
          parcel_number: "GN-3-2022-000100",
          address_text: "Kamsar, Boké, Guinea",
          area_m2: 1200,
          land_use: "Industrial",
          status: "DISPUTED",
          has_active_dispute: true,
          current_owner: "Compagnie Minière de Kamsar",
          current_title_number: "TIT-2021-002300",
          prefecture_code: "GN3"
        },
        {
          parcel_number: "GN-22-2021-000050",
          address_text: "Labé centre, Labé, Guinea",
          area_m2: 650,
          land_use: "Residential",
          status: "PENDING",
          has_active_dispute: false,
          current_owner: "Unknown (registration in progress)",
          current_title_number: null,
          prefecture_code: "GN22"
        },
        {
          parcel_number: "GN-29-2020-000200",
          address_text: "Nzérékoré, Guinée Forestière",
          area_m2: 900,
          land_use: "Agricultural",
          status: "REGISTERED",
          has_active_dispute: false,
          current_owner: "Coopérative Agricole de Guinée Forestière",
          current_title_number: "TIT-2020-000900",
          prefecture_code: "GN29"
        },
        {
          parcel_number: "GN-5-2019-000023",
          address_text: "Km 36, Coyah, Kindia, Guinea",
          area_m2: 375.5,
          land_use: "Residential",
          status: "REGISTERED",
          has_active_dispute: false,
          current_owner: "Famille Camara",
          current_title_number: "TIT-2019-000123",
          prefecture_code: "GN5"
        },
        {
          parcel_number: "GN-9-2021-000150",
          address_text: "Tanéné, Dubréka, Kindia, Guinea",
          area_m2: 820,
          land_use: "Mixed use",
          status: "PENDING",
          has_active_dispute: false,
          current_owner: "Société Agro-Export Dubréka",
          current_title_number: null,
          prefecture_code: "GN9"
        },
        {
          parcel_number: "GN-11-2018-000008",
          address_text: "Forécariah centre, Kindia, Guinea",
          area_m2: 1500,
          land_use: "Agricultural",
          status: "REGISTERED",
          has_active_dispute: false,
          current_owner: "Groupement Maraîcher de Forécariah",
          current_title_number: "TIT-2018-000088",
          prefecture_code: "GN11"
        },
        {
          parcel_number: "GN-2-2019-000033",
          address_text: "Boffa centre, Boké, Guinea",
          area_m2: 600,
          land_use: "Residential",
          status: "DISPUTED",
          has_active_dispute: true,
          current_owner: "Famille Bangoura",
          current_title_number: "TIT-2017-000560",
          prefecture_code: "GN2"
        },
        {
          parcel_number: "GN-15-2022-000300",
          address_text: "Kankan ville, Kankan, Guinea",
          area_m2: 2000,
          land_use: "Commercial",
          status: "REGISTERED",
          has_active_dispute: false,
          current_owner: "Société de Services de Kankan",
          current_title_number: "TIT-2022-001230",
          prefecture_code: "GN15"
        },
        {
          parcel_number: "GN-6-2016-000011",
          address_text: "Quartier central, Dabola, Faranah, Guinea",
          area_m2: 950,
          land_use: "Residential",
          status: "REGISTERED",
          has_active_dispute: false,
          current_owner: "Coopérative d’Habitat de Dabola",
          current_title_number: "TIT-2016-000980",
          prefecture_code: "GN6"
        },
        {
          parcel_number: "GN-7-2023-000007",
          address_text: "Plateau de Dalaba, Mamou, Guinea",
          area_m2: 720,
          land_use: "Tourism",
          status: "PENDING",
          has_active_dispute: false,
          current_owner: "Projet Écotouristique de Dalaba",
          current_title_number: null,
          prefecture_code: "GN7"
        },
        {
          parcel_number: "GN-1-2015-000500",
          address_text: "Périphérie de Beyla, Nzérékoré, Guinea",
          area_m2: 5000,
          land_use: "Agricultural",
          status: "REGISTERED",
          has_active_dispute: false,
          current_owner: "Société Forestière de Beyla",
          current_title_number: "TIT-2015-000430",
          prefecture_code: "GN1"
        }
      ];

      const sampleTransactions = [
        {
          transaction_number: "TXN-2023-000045",
          transaction_type: "SALE",
          signed_date: "2023-06-10",
          registered_date: "2023-06-30",
          status: "REGISTERED",
          parcel_number: "GN-4-2023-000001",
          seller_name: "République de Guinée (État)",
          buyer_name: "Société Immobilière de Guinée"
        },
        {
          transaction_number: "TXN-2022-000310",
          transaction_type: "MORTGAGE",
          signed_date: "2022-03-02",
          registered_date: "2022-03-20",
          status: "REGISTERED",
          parcel_number: "GN-3-2022-000100",
          seller_name: "Compagnie Minière de Kamsar",
          buyer_name: "Banque Guinéenne de l’Habitat"
        },
        {
          transaction_number: "TXN-2021-000120",
          transaction_type: "INHERITANCE",
          signed_date: "2021-11-15",
          registered_date: null,
          status: "UNDER_REVIEW",
          parcel_number: "GN-22-2021-000050",
          seller_name: "Succession Diallo",
          buyer_name: "Famille Diallo"
        },
        {
          transaction_number: "TXN-2020-000210",
          transaction_type: "SALE",
          signed_date: "2020-02-11",
          registered_date: "2020-02-28",
          status: "REGISTERED",
          parcel_number: "GN-29-2020-000200",
          seller_name: "Commune de Nzérékoré",
          buyer_name: "Coopérative Agricole de Guinée Forestière"
        },
        {
          transaction_number: "TXN-2019-000560",
          transaction_type: "SALE",
          signed_date: "2019-04-15",
          registered_date: "2019-05-02",
          status: "REGISTERED",
          parcel_number: "GN-2-2019-000033",
          seller_name: "Famille Touré",
          buyer_name: "Famille Bangoura"
        },
        {
          transaction_number: "TXN-2018-000088",
          transaction_type: "SALE",
          signed_date: "2018-01-20",
          registered_date: "2018-02-10",
          status: "REGISTERED",
          parcel_number: "GN-11-2018-000008",
          seller_name: "Commune de Forécariah",
          buyer_name: "Groupement Maraîcher de Forécariah"
        },
        {
          transaction_number: "TXN-2016-000980",
          transaction_type: "SALE",
          signed_date: "2016-06-18",
          registered_date: "2016-07-01",
          status: "REGISTERED",
          parcel_number: "GN-6-2016-000011",
          seller_name: "Famille Keïta",
          buyer_name: "Coopérative d’Habitat de Dabola"
        },
        {
          transaction_number: "TXN-2015-000430",
          transaction_type: "SALE",
          signed_date: "2015-09-03",
          registered_date: "2015-09-20",
          status: "REGISTERED",
          parcel_number: "GN-1-2015-000500",
          seller_name: "Famille Kourouma",
          buyer_name: "Société Forestière de Beyla"
        },
        {
          transaction_number: "TXN-2022-001230",
          transaction_type: "SALE",
          signed_date: "2022-10-12",
          registered_date: "2022-10-30",
          status: "REGISTERED",
          parcel_number: "GN-15-2022-000300",
          seller_name: "Commune Urbaine de Kankan",
          buyer_name: "Société de Services de Kankan"
        },
        {
          transaction_number: "TXN-2020-000523",
          transaction_type: "MORTGAGE",
          signed_date: "2020-08-05",
          registered_date: "2020-08-18",
          status: "REGISTERED",
          parcel_number: "GN-5-2019-000023",
          seller_name: "Famille Camara",
          buyer_name: "Banque Populaire de Guinée"
        },
        {
          transaction_number: "TXN-2021-000765",
          transaction_type: "SALE",
          signed_date: "2021-03-22",
          registered_date: "2021-04-10",
          status: "REGISTERED",
          parcel_number: "GN-9-2021-000150",
          seller_name: "Famille Sylla",
          buyer_name: "Société Agro-Export Dubréka"
        },
        {
          transaction_number: "TXN-2023-000901",
          transaction_type: "OTHER",
          signed_date: "2023-01-15",
          registered_date: null,
          status: "UNDER_REVIEW",
          parcel_number: "GN-7-2023-000007",
          seller_name: "Commune de Dalaba",
          buyer_name: "Projet Écotouristique de Dalaba"
        }
      ];

      let currentLang = "en";
      let accounts = [];
      let currentUser = null;
      let ministries = [];
      let prefecturesData = [];
      let lastParcelResult = null;
      let lastTransactionResult = null;
      let selectedProductCode = "FULL_PROPERTY_REPORT";
      let currentOrder = null;
      let currentPayment = null;

      function getNestedTranslation(lang, path) {
        const parts = path.split(".");
        let value = translations[lang];
        for (let i = 0; i < parts.length; i++) {
          if (!value || typeof value !== "object") return null;
          value = value[parts[i]];
        }
        return typeof value === "string" ? value : null;
      }

      function applyTranslations() {
        const nodes = document.querySelectorAll("[data-i18n]");
        nodes.forEach((node) => {
          const key = node.getAttribute("data-i18n");
          const text = getNestedTranslation(currentLang, key);
          if (text !== null) {
            node.textContent = text;
          }
        });

        const placeholders = document.querySelectorAll("[data-i18n-placeholder]");
        placeholders.forEach((node) => {
          const key = node.getAttribute("data-i18n-placeholder");
          const text = getNestedTranslation(currentLang, key);
          if (text !== null) {
            node.setAttribute("placeholder", text);
          }
        });
      }

      function updateLanguageButtons() {
        const btnEn = document.getElementById("lang-en");
        const btnFr = document.getElementById("lang-fr");
        if (!btnEn || !btnFr) return;
        if (currentLang === "en") {
          btnEn.classList.add("text-emerald-300", "bg-emerald-500/15", "border", "border-emerald-500/40");
          btnEn.classList.remove("text-slate-400");
          btnFr.classList.remove("text-emerald-300", "bg-emerald-500/15", "border-emerald-500/40");
          btnFr.classList.add("text-slate-400");
        } else {
          btnFr.classList.add("text-emerald-300", "bg-emerald-500/15", "border", "border-emerald-500/40");
          btnFr.classList.remove("text-slate-400");
          btnEn.classList.remove("text-emerald-300", "bg-emerald-500/15", "border-emerald-500/40");
          btnEn.classList.add("text-slate-400");
        }
      }

      function formatCurrency(amount) {
        if (typeof amount !== "number") return "";
        try {
          return amount.toLocaleString(currentLang === "fr" ? "fr-FR" : "en-GB") + " GNF";
        } catch (e) {
          return amount + " GNF";
        }
      }

      function loadState() {
        try {
          const rawAcc = localStorage.getItem("le_record_accounts_v1");
          accounts = rawAcc ? JSON.parse(rawAcc) : [];
          if (!Array.isArray(accounts)) accounts = [];
        } catch (e) {
          accounts = [];
        }

        // Seed demo admin account if missing
        if (!accounts.some((a) => a.username === "admin")) {
          accounts.push({
            username: "admin",
            password: "admin",
            role: "ADMIN",
            user_type: "STAFF",
            organization_name: "Registry Super Admin",
            email: "admin@example.com",
            phone: "+224600000000",
            is_ministry_worker: true,
            is_verified: true,
            verify_method: "email"
          });
        }

        try {
          const rawUser = localStorage.getItem("le_record_current_user_v1");
          currentUser = rawUser ? JSON.parse(rawUser) : null;
        } catch (e) {
          currentUser = null;
        }

        if (currentUser && !accounts.some((a) => a.username === currentUser.username)) {
          currentUser = null;
        }

        try {
          const rawPref = localStorage.getItem("le_record_prefectures_v1");
          prefecturesData = rawPref ? JSON.parse(rawPref) : defaultPrefectures;
          if (!Array.isArray(prefecturesData) || !prefecturesData.length) {
            prefecturesData = defaultPrefectures;
          }
        } catch (e) {
          prefecturesData = defaultPrefectures;
        }

        try {
          const rawMin = localStorage.getItem("le_record_ministries_v1");
          ministries = rawMin ? JSON.parse(rawMin) : defaultMinistries;
          if (!Array.isArray(ministries) || !ministries.length) {
            ministries = defaultMinistries;
          }
        } catch (e) {
          ministries = defaultMinistries;
        }

        // Ensure removed ministries like 'MOF' or any Economy/Finance ministry no longer appear, even if stored previously
        ministries = ministries.filter((m) => {
          if (!m) return false;
          const nameEn = (m.name_en || "").toLowerCase();
          const nameFr = (m.name_fr || "").toLowerCase();
          const isOldMofId = m.id === "MOF" || m.id === "MEF";
          const isEconomyFinance =
            nameEn.includes("economy and finance") ||
            nameEn.includes("economy & finance") ||
            (nameEn.includes("economy") && nameEn.includes("finance")) ||
            nameFr.includes("économie") ||
            nameFr.includes("economie") ||
            nameFr.includes("finances") ||
            nameFr.includes("finance");
          return !isOldMofId && !isEconomyFinance;
        });
      }

      function saveAccounts() {
        try {
          localStorage.setItem("le_record_accounts_v1", JSON.stringify(accounts));
        } catch (e) {}
      }

      function saveCurrentUser() {
        try {
          if (currentUser) {
            localStorage.setItem("le_record_current_user_v1", JSON.stringify(currentUser));
          } else {
            localStorage.removeItem("le_record_current_user_v1");
          }
        } catch (e) {}
      }

      function savePrefectures() {
        try {
          localStorage.setItem("le_record_prefectures_v1", JSON.stringify(prefecturesData));
        } catch (e) {}
      }

      function saveMinistries() {
        try {
          localStorage.setItem("le_record_ministries_v1", JSON.stringify(ministries));
        } catch (e) {}
      }

      function isAdmin() {
        return !!(currentUser && currentUser.role === "ADMIN");
      }

      function updateDeveloperVisibility() {
        const devNavLink = document.getElementById("navDevelopersLink");
        const heroTechCta = document.getElementById("heroTechCta");
        const devSection = document.getElementById("developers");
        const admin = isAdmin();
        [devNavLink, heroTechCta, devSection].forEach((el) => {
          if (!el) return;
          if (admin) {
            el.classList.remove("hidden");
          } else {
            el.classList.add("hidden");
          }
        });
      }

      function updateAuthUI() {
        const tAcc = translations[currentLang].accounts;
        const headerAccountBtn = document.getElementById("headerAccountBtn");
        const authStatusText = document.getElementById("authStatusText");
        const signOutBtn = document.getElementById("signOutBtn");
        const adminBadge = document.getElementById("adminBadge");

        if (currentUser) {
          const roleLabel = isAdmin() ? "Admin" : (currentUser.user_type || "USER");
          const verifiedFlag = currentUser.is_verified ? "✓" : "!";
          const verifiedLabel = currentUser.is_verified
            ? (currentLang === "fr" ? "vérifié" : "verified")
            : (currentLang === "fr" ? "non vérifié" : "not verified");
          if (authStatusText) {
            authStatusText.textContent = `${tAcc.signedInAs} (${roleLabel}, ${verifiedFlag} ${verifiedLabel})`;
          }
          if (signOutBtn) signOutBtn.classList.remove("hidden");
          if (adminBadge) {
            if (isAdmin()) {
              adminBadge.classList.remove("hidden");
            } else {
              adminBadge.classList.add("hidden");
            }
          }
        } else {
          if (authStatusText) {
            authStatusText.textContent = tAcc.notSignedIn;
          }
          if (signOutBtn) signOutBtn.classList.add("hidden");
          if (adminBadge) {
            adminBadge.classList.add("hidden");
          }
        }

        if (headerAccountBtn) {
          headerAccountBtn.textContent = translations[currentLang].nav.login;
        }

        updateSearchAccess();
        renderMinistryAccess();
        updateDeveloperVisibility();
      }

      function updateSearchAccess() {
        const gate = document.getElementById("searchGate");
        const inner = document.getElementById("searchInner");
        const tSearch = translations[currentLang].search;
        if (!gate || !inner) return;

        const gateTitle = document.getElementById("searchGateTitle");
        const gateBody = document.getElementById("searchGateBody");

        if (!currentUser) {
          gate.classList.remove("hidden");
          inner.classList.add("opacity-40", "pointer-events-none");
          if (gateTitle) gateTitle.textContent = tSearch.loginRequiredTitle;
          if (gateBody) gateBody.textContent = tSearch.loginRequiredBody;
        } else {
          gate.classList.add("hidden");
          inner.classList.remove("opacity-40", "pointer-events-none");
        }
      }

      function renderPrefectures() {
        const container = document.getElementById("prefecturesContainer");
        if (!container) return;

        const tCommon = translations[currentLang].common;
        const tDiv = translations[currentLang].divisions;
        const tAdmin = translations[currentLang].admin;
        const admin = isAdmin();

        let html = "";

        html += `<div class="mb-4 text-xs text-slate-300 space-y-1">
          <p>${tDiv.macroRegionIntro}</p>
          <ul class="list-disc list-inside text-[11px] text-slate-300">
            <li>${tDiv.macroBG}</li>
            <li>${tDiv.macroMG}</li>
            <li>${tDiv.macroHG}</li>
            <li>${tDiv.macroFG}</li>
          </ul>
        </div>`;

        macroRegions.forEach((mr) => {
          const name = currentLang === "fr" ? mr.name_fr : mr.name_en;
          const prefs = prefecturesData.filter((p) => p.macro_region_key === mr.key);
          if (!prefs.length) return;
          html += `<div class="bg-slate-900/80 border border-slate-800 rounded-xl p-4 sm:p-5">
            <div class="flex items-center justify-between gap-2 mb-2">
              <h3 class="text-sm font-semibold text-emerald-300">${name}</h3>
              <span class="text-[11px] text-slate-400">${tDiv.prefectureTableTitle}</span>
            </div>
            <div class="overflow-x-auto">
              <table class="min-w-full text-[11px] text-left text-slate-200">
                <thead class="text-slate-400 border-b border-slate-800">
                  <tr>
                    <th class="py-1 pr-3">${tCommon.prefectureCode}</th>
                    <th class="py-1 pr-3">${tCommon.prefecture}</th>
                    <th class="py-1 pr-3">${tCommon.administrativeRegion}</th>
                    ${admin ? `<th class="py-1 pr-3"></th>` : ""}
                  </tr>
                </thead>
                <tbody>`;
          prefs
            .slice()
            .sort((a, b) => a.id - b.id)
            .forEach((p) => {
              html += `<tr class="border-b border-slate-900/60">
                  <td class="py-1 pr-3 text-slate-200">${p.code}</td>
                  <td class="py-1 pr-3">${p.name}</td>
                  <td class="py-1 pr-3 text-slate-300">${p.administrative_region}</td>
                  ${admin
                    ? `<td class="py-1 pr-3 text-right"><button type="button" data-pref-code="${p.code}" class="js-edit-pref text-emerald-300 hover:text-emerald-200 underline decoration-emerald-500/70">${tAdmin.editPrefectureButton}</button></td>`
                    : ""}
                </tr>`;
            });

          html += `</tbody></table></div></div>`;
        });

        container.innerHTML = html;

        if (isAdmin()) {
          container.querySelectorAll(".js-edit-pref").forEach((btn) => {
            btn.addEventListener("click", () => {
              const code = btn.getAttribute("data-pref-code");
              if (!code) return;
              editPrefecture(code);
            });
          });
        }
      }

      function editPrefecture(code) {
        const tAdmin = translations[currentLang].admin;
        const pref = prefecturesData.find((p) => p.code === code);
        if (!pref) return;

        const newName = window.prompt(tAdmin.editPrefecturePromptName, pref.name);
        if (newName && newName.trim()) {
          pref.name = newName.trim();
        }
        const newCode = window.prompt(tAdmin.editPrefecturePromptCode, pref.code);
        if (newCode && newCode.trim()) {
          pref.code = newCode.trim();
        }
        savePrefectures();
        renderPrefectures();
        renderPrefectureMapList();
      }

      function renderPrefectureMapList() {
        const listEl = document.getElementById("prefectureMapList");
        const iframe = document.getElementById("prefectureMapIframe");
        const infoBox = document.getElementById("prefectureMapInfo");
        if (!listEl) return;

        if (infoBox) {
          const tDiv = translations[currentLang].divisions;
          infoBox.innerHTML = `<p class="text-[11px] text-slate-300">${tDiv.mapInfoPlaceholder}</p>`;
        }

        const sorted = prefecturesData
          .slice()
          .sort((a, b) => a.id - b.id);

        const labelRegion = translations[currentLang].common.administrativeRegion;

        listEl.innerHTML = "";
        sorted.forEach((p) => {
          const btn = document.createElement("button");
          btn.type = "button";
          btn.className =
            "w-full text-left px-2 py-1 rounded hover:bg-slate-800 flex items-center justify-between gap-2";
          const mainLabel = `${p.code} · ${p.name}`;
          const subLabel = p.administrative_region
            ? `${labelRegion}: ${p.administrative_region}`
            : "";
          btn.innerHTML = `
            <span class="text-[11px] text-slate-100">${mainLabel}</span>
            <span class="text-[10px] text-slate-400">${subLabel}</span>
          `;

          btn.addEventListener("click", () => {
            // Always search within Guinea so the map stays focused on the national territory
            const baseQuery = p.administrative_region
              ? `${p.name}, ${p.administrative_region}, Guinea`
              : `${p.name}, Guinea`;
            const query = encodeURIComponent(baseQuery);

            if (iframe) {
              iframe.src = `https://www.google.com/maps?q=${query}&output=embed`;
            }

            if (infoBox) {
              const tCommon = translations[currentLang].common;
              infoBox.innerHTML = `
                <div class="flex flex-wrap items-center justify-between gap-2">
                  <div class="text-[11px] text-slate-100 font-semibold">${p.code} · ${p.name}</div>
                  <div class="text-[10px] text-slate-400">${tCommon.administrativeRegion}: ${p.administrative_region || "—"}</div>
                </div>
              `;
            }

            window.open(`https://www.openstreetmap.org/search?query=${query}`, "_blank");
          });

          listEl.appendChild(btn);
        });
      }

      function renderMinistryAccess() {
        const container = document.getElementById("ministriesContainer");
        if (!container) return;
        const tAdmin = translations[currentLang].admin;
        const admin = isAdmin();

        let html = "";
        html += `<p class="mb-2 text-[11px] ${admin ? "text-emerald-300" : "text-slate-400"}">${admin ? tAdmin.adminOnlyNote : tAdmin.notAdminNote}</p>`;

        ministries.forEach((m) => {
          const name = currentLang === "fr" ? m.name_fr : m.name_en;
          const can = !!m.can_add_parcels;
          html += `<div class="flex items-center justify-between gap-3 border border-slate-800 rounded-lg px-3 py-2 bg-slate-950/60">
            <div class="text-[11px]">
              <div class="font-semibold text-slate-100">${name}</div>
              <div class="text-slate-400">${tAdmin.canCreateParcels}: <span class="font-semibold ${can ? "text-emerald-300" : "text-amber-300"}">${can ? tAdmin.yesShort : tAdmin.noShort}</span></div>
            </div>
            ${admin
              ? `<button type="button" data-min-id="${m.id}" class="js-toggle-min inline-flex items-center px-2 py-1 rounded-md text-[11px] border ${can ? "border-amber-400 text-amber-300" : "border-emerald-400 text-emerald-300"}">${can ? tAdmin.toggleRevoke : tAdmin.toggleGrant}</button>`
              : ""}
          </div>`;
        });

        container.innerHTML = html;

        if (admin) {
          container.querySelectorAll(".js-toggle-min").forEach((btn) => {
            btn.addEventListener("click", () => {
              const id = btn.getAttribute("data-min-id");
              const m = ministries.find((x) => x.id === id);
              if (!m) return;
              m.can_add_parcels = !m.can_add_parcels;
              saveMinistries();
              renderMinistryAccess();
            });
          });
        }
      }

      function renderParcelResult() {
        const container = document.getElementById("parcelResultContainer");
        if (!container) return;
        if (!lastParcelResult) {
          container.classList.add("hidden");
          container.innerHTML = "";
          return;
        }

        const t = translations[currentLang];
        const tCommon = t.common;
        const tSearch = t.search;
        const tStatuses = t.statuses;

        if (lastParcelResult.notFound) {
          container.classList.remove("hidden");
          container.innerHTML = `
            <h3 class="text-sm font-semibold text-amber-300 mb-1">${tSearch.notFoundTitle}</h3>
            <p class="text-xs text-slate-300">${tSearch.notFoundBody}</p>
          `;
          return;
        }

        const p = lastParcelResult;
        const statusLabel = tStatuses[p.status] || p.status;

        let prefectureDisplay = "—";
        let macroDisplay = "—";
        let adminRegionDisplay = "—";

        if (p.prefecture_code) {
          const pref = prefecturesData.find((pf) => pf.code === p.prefecture_code);
          if (pref) {
            prefectureDisplay = `${pref.code} · ${pref.name}`;
            adminRegionDisplay = pref.administrative_region || "—";
            const mr = macroRegions.find((m) => m.key === pref.macro_region_key);
            if (mr) {
              macroDisplay = currentLang === "fr" ? mr.name_fr : mr.name_en;
            }
          }
        }

        container.classList.remove("hidden");
        container.innerHTML = `
          <div class="flex items-center justify-between gap-2 mb-2">
            <h3 class="text-sm font-semibold text-slate-100">${tSearch.parcelResultTitle} · ${p.parcel_number}</h3>
            <span class="inline-flex items-center rounded-full px-2 py-0.5 text-[11px] border ${p.status === "DISPUTED" ? "border-amber-400 text-amber-300" : "border-emerald-400 text-emerald-300"}">
              ${statusLabel}
            </span>
          </div>
          <dl class="grid grid-cols-2 gap-x-3 gap-y-1.5 text-[11px] text-slate-300">
            <div>
              <dt class="text-slate-400">${tCommon.address}</dt>
              <dd>${p.address_text}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tCommon.area}</dt>
              <dd>${p.area_m2.toLocaleString(currentLang === "fr" ? "fr-FR" : "en-GB")}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tCommon.landUse}</dt>
              <dd>${p.land_use || "—"}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tSearch.hasActiveDispute}</dt>
              <dd>${p.has_active_dispute ? tCommon.yes : tCommon.no}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tCommon.prefecture}</dt>
              <dd>${prefectureDisplay}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tCommon.macroRegion}</dt>
              <dd>${macroDisplay}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tCommon.administrativeRegion}</dt>
              <dd>${adminRegionDisplay}</dd>
            </div>
            <div class="col-span-2">
              <dt class="text-slate-400">${tCommon.owner}</dt>
              <dd class="font-medium text-slate-100">${p.current_owner || "—"}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tCommon.titleNumber}</dt>
              <dd>${p.current_title_number || "—"}</dd>
            </div>
          </dl>
          <div class="mt-3">
            <button type="button" class="inline-flex items-center gap-1 text-[11px] text-emerald-300 hover:text-emerald-200 underline decoration-emerald-500/70" id="orderFromParcelBtn">
              ${tSearch.viewOrderOptions}
            </button>
          </div>
        `;

        const btn = document.getElementById("orderFromParcelBtn");
        if (btn) {
          btn.addEventListener("click", () => {
            const reportsSection = document.getElementById("reports");
            if (reportsSection) reportsSection.scrollIntoView({ behavior: "smooth" });
          });
        }
      }

      function renderTransactionResult() {
        const container = document.getElementById("transactionResultContainer");
        if (!container) return;
        if (!lastTransactionResult) {
          container.classList.add("hidden");
          container.innerHTML = "";
          return;
        }

        const t = translations[currentLang];
        const tSearch = t.search;
        const tCommon = t.common;
        const tTxnTypes = t.txnTypes;
        const tStatuses = t.statuses;

        if (lastTransactionResult.notFound) {
          container.classList.remove("hidden");
          container.innerHTML = `
            <h3 class="text-sm font-semibold text-amber-300 mb-1">${tSearch.notFoundTitle}</h3>
            <p class="text-xs text-slate-300">${tSearch.notFoundBody}</p>
          `;
          return;
        }

        const tx = lastTransactionResult;
        const typeLabel = tTxnTypes[tx.transaction_type] || tx.transaction_type;
        const statusLabel = tStatuses[tx.status] || tx.status;

        let prefectureDisplay = "—";
        let macroDisplay = "—";
        let adminRegionDisplay = "—";

        const linkedParcel = sampleParcels.find((p) => p.parcel_number === tx.parcel_number);
        if (linkedParcel && linkedParcel.prefecture_code) {
          const pref = prefecturesData.find((pf) => pf.code === linkedParcel.prefecture_code);
          if (pref) {
            prefectureDisplay = `${pref.code} · ${pref.name}`;
            adminRegionDisplay = pref.administrative_region || "—";
            const mr = macroRegions.find((m) => m.key === pref.macro_region_key);
            if (mr) {
              macroDisplay = currentLang === "fr" ? mr.name_fr : mr.name_en;
            }
          }
        }

        container.classList.remove("hidden");
        container.innerHTML = `
          <div class="flex items-center justify-between gap-2 mb-2">
            <h3 class="text-sm font-semibold text-slate-100">${tSearch.transactionResultTitle} · ${tx.transaction_number}</h3>
            <span class="inline-flex items-center rounded-full px-2 py-0.5 text-[11px] border ${tx.status === "REGISTERED" ? "border-emerald-400 text-emerald-300" : "border-slate-500 text-slate-200"}">
              ${statusLabel}
            </span>
          </div>
          <dl class="grid grid-cols-2 gap-x-3 gap-y-1.5 text-[11px] text-slate-300">
            <div>
              <dt class="text-slate-400">${tCommon.transactionType}</dt>
              <dd>${typeLabel}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${translations[currentLang].reports.parcelNumberLabel}</dt>
              <dd>${tx.parcel_number}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tCommon.seller}</dt>
              <dd>${tx.seller_name || "—"}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tCommon.buyer}</dt>
              <dd>${tx.buyer_name || "—"}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tCommon.signedOn}</dt>
              <dd>${tx.signed_date}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tCommon.registeredOn}</dt>
              <dd>${tx.registered_date || "—"}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tCommon.prefecture}</dt>
              <dd>${prefectureDisplay}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tCommon.macroRegion}</dt>
              <dd>${macroDisplay}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tCommon.administrativeRegion}</dt>
              <dd>${adminRegionDisplay}</dd>
            </div>
          </dl>
          <div class="mt-3">
            <button type="button" class="inline-flex items-center gap-1 text-[11px] text-emerald-300 hover:text-emerald-200 underline decoration-emerald-500/70" id="orderFromTransactionBtn">
              ${tSearch.viewOrderOptions}
            </button>
          </div>
        `;

        const btn = document.getElementById("orderFromTransactionBtn");
        if (btn) {
          btn.addEventListener("click", () => {
            const reportsSection = document.getElementById("reports");
            if (reportsSection) reportsSection.scrollIntoView({ behavior: "smooth" });
          });
        }
      }

      function renderEmptyOrderSummary() {
        const orderSummaryEl = document.getElementById("orderSummary");
        if (!orderSummaryEl) return;
        const tReports = translations[currentLang].reports;
        orderSummaryEl.innerHTML = `
          <p class="text-[11px] text-slate-400">
            <strong>${tReports.noOrderYetTitle}</strong><br>
            ${tReports.noOrderYetBody}
          </p>
        `;
      }

      function renderOrderSummary() {
        const orderSummaryEl = document.getElementById("orderSummary");
        if (!orderSummaryEl) return;
        const t = translations[currentLang];
        const tReports = t.reports;

        if (!currentOrder) {
          renderEmptyOrderSummary();
          return;
        }

        const productLabel =
          currentOrder.productCode === "FULL_PROPERTY_REPORT" ? tReports.fullReport : tReports.certExtract;
        const orderStatusLabel = t.orderStatus[currentOrder.status] || currentOrder.status;

        orderSummaryEl.innerHTML = `
          <dl class="grid grid-cols-2 gap-x-3 gap-y-1.5 text-[11px]">
            <div class="col-span-2">
              <dt class="text-slate-400">${tReports.chooseProduct}</dt>
              <dd class="text-xs text-slate-100 font-medium">${productLabel}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tReports.parcelNumberLabel}</dt>
              <dd class="text-xs">${currentOrder.parcel_number || "—"}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tReports.transactionNumberLabel}</dt>
              <dd class="text-xs">${currentOrder.transaction_number || "—"}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tReports.amountLabel}</dt>
              <dd class="text-xs font-semibold text-emerald-300">${formatCurrency(currentOrder.amount_gnf)}</dd>
            </div>
            <div>
              <dt class="text-slate-400">${tReports.statusLabel}</dt>
              <dd class="text-xs">${orderStatusLabel}</dd>
            </div>
          </dl>
        `;
      }

      function selectProduct(code) {
        selectedProductCode = code;
        const fullBtn = document.getElementById("product-full");
        const certBtn = document.getElementById("product-cert");
        if (!fullBtn || !certBtn) return;

        if (code === "FULL_PROPERTY_REPORT") {
          fullBtn.classList.add("border-emerald-500/60", "bg-slate-900/80");
          fullBtn.classList.remove("border-slate-800", "bg-slate-900/60");
          certBtn.classList.add("border-slate-800", "bg-slate-900/60");
          certBtn.classList.remove("border-emerald-500/60", "bg-slate-900/80");
        } else {
          certBtn.classList.add("border-emerald-500/60", "bg-slate-900/80");
          certBtn.classList.remove("border-slate-800", "bg-slate-900/60");
          fullBtn.classList.add("border-slate-800", "bg-slate-900/60");
          fullBtn.classList.remove("border-emerald-500/60", "bg-slate-900/80");
        }
      }

      function createDemoOrder() {
        const tReports = translations[currentLang].reports;
        const orderSummaryEl = document.getElementById("orderSummary");
        const paymentMessageEl = document.getElementById("paymentMessage");
        if (!orderSummaryEl) return;

        if (!currentUser) {
          if (orderSummaryEl) {
            orderSummaryEl.innerHTML = `<p class="text-[11px] text-amber-300">${tReports.authRequiredForOrder}</p>`;
          }
          return;
        }

        const hasParcel = lastParcelResult && !lastParcelResult.notFound;
        const hasTxn = lastTransactionResult && !lastTransactionResult.notFound;

        if (!hasParcel && !hasTxn) {
          currentOrder = null;
          orderSummaryEl.innerHTML = `
            <p class="text-[11px] text-amber-300">${tReports.noOrderYetBody}</p>
          `;
          return;
        }

        const productPrices = {
          FULL_PROPERTY_REPORT: 100000,
          CERT_EXTRACT: 50000
        };

        const id = "ORD-" + Math.floor(100000 + Math.random() * 900000);
        const parcelNumber = hasParcel
          ? lastParcelResult.parcel_number
          : hasTxn
          ? lastTransactionResult.parcel_number
          : "";
        const txnNumber = hasTxn ? lastTransactionResult.transaction_number : "";

        currentOrder = {
          id,
          productCode: selectedProductCode,
          parcel_number: parcelNumber,
          transaction_number: txnNumber,
          amount_gnf: productPrices[selectedProductCode] || 0,
          status: "PENDING"
        };

        currentPayment = null;
        const timeline = document.getElementById("paymentTimeline");
        if (timeline) {
          timeline.innerHTML = "";
        }
        if (paymentMessageEl) {
          paymentMessageEl.textContent = "";
          paymentMessageEl.classList.remove("text-emerald-300", "text-amber-300");
        }
        const sampleReportContainer = document.getElementById("sampleReportLinkContainer");
        if (sampleReportContainer) {
          sampleReportContainer.classList.add("hidden");
        }
        const qrContainer = document.getElementById("qrCodeContainer");
        const qrImg = document.getElementById("qrCodeImage");
        if (qrContainer) {
          qrContainer.classList.add("hidden");
        }
        if (qrImg) {
          qrImg.removeAttribute("src");
        }

        renderOrderSummary();
      }

      function startDemoPayment() {
        const t = translations[currentLang];
        const tReports = t.reports;
        const tPaymentStatus = t.paymentStatus;
        const paymentMessageEl = document.getElementById("paymentMessage");
        const timelineEl = document.getElementById("paymentTimeline");
        const sampleReportContainer = document.getElementById("sampleReportLinkContainer");
        const startPaymentBtn = document.getElementById("startPaymentBtn");
        const phoneInput = document.getElementById("omPhoneInput");

        if (!currentUser) {
          if (paymentMessageEl) {
            paymentMessageEl.textContent = tReports.authRequiredForOrder;
            paymentMessageEl.classList.remove("text-emerald-300");
            paymentMessageEl.classList.add("text-amber-300");
          }
          return;
        }

        if (!currentOrder) {
          if (paymentMessageEl) {
            paymentMessageEl.textContent = tReports.noOrderForPayment;
            paymentMessageEl.classList.remove("text-emerald-300");
            paymentMessageEl.classList.add("text-amber-300");
          }
          return;
        }

        const phone = phoneInput ? phoneInput.value.trim() : "";
        if (!phone || !phone.startsWith("+224")) {
          if (paymentMessageEl) {
            paymentMessageEl.textContent = tReports.phoneRequired;
            paymentMessageEl.classList.remove("text-emerald-300");
            paymentMessageEl.classList.add("text-amber-300");
          }
          return;
        }

        currentPayment = {
          id: "PAY-" + Math.floor(100000 + Math.random() * 900000),
          method: "ORANGE_MONEY",
          status: "PENDING",
          phone
        };

        if (timelineEl) {
          timelineEl.innerHTML = "";
        }
        if (paymentMessageEl) {
          paymentMessageEl.textContent = "";
          paymentMessageEl.classList.remove("text-emerald-300", "text-amber-300");
        }
        if (sampleReportContainer) {
          sampleReportContainer.classList.add("hidden");
        }
        if (startPaymentBtn) {
          startPaymentBtn.disabled = true;
          startPaymentBtn.classList.add("opacity-60", "cursor-not-allowed");
        }

        const addTimelineItem = (step, label) => {
          if (!timelineEl) return;
          const li = document.createElement("li");
          li.innerHTML = `<span class="font-semibold text-emerald-300 mr-1">${step}.</span>${label}`;
          timelineEl.appendChild(li);
        };

        addTimelineItem("1", tReports.timelineCreated);

        window.setTimeout(() => {
          addTimelineItem("2", tReports.timelineInit);
        }, 700);

        window.setTimeout(() => {
          currentPayment.status = "SUCCESS";
          currentOrder.status = "PAID";
          renderOrderSummary();
          addTimelineItem("3", tReports.timelineWebhook);
        }, 1600);

        window.setTimeout(() => {
          addTimelineItem("4", tReports.timelineReport);
          if (sampleReportContainer) {
            sampleReportContainer.classList.remove("hidden");
          }
          const qrContainer = document.getElementById("qrCodeContainer");
          const qrImg = document.getElementById("qrCodeImage");
          if (qrContainer && qrImg && currentOrder) {
            const payload = {
              order_id: currentOrder.id,
              parcel_number: currentOrder.parcel_number || null,
              transaction_number: currentOrder.transaction_number || null,
              product_code: currentOrder.productCode
            };
            const dataStr = JSON.stringify(payload);
            const qrUrl = `https://api.qrserver.com/v1/create-qr-code/?size=160x160&data=${encodeURIComponent(dataStr)}`;
            qrImg.src = qrUrl;
            qrContainer.classList.remove("hidden");
          }
          if (paymentMessageEl) {
            paymentMessageEl.textContent = `${tPaymentStatus.SUCCESS} · ${formatCurrency(currentOrder.amount_gnf)} Orange Money (demo).`;
            paymentMessageEl.classList.remove("text-amber-300");
            paymentMessageEl.classList.add("text-emerald-300");
          }
          if (startPaymentBtn) {
            startPaymentBtn.disabled = false;
            startPaymentBtn.classList.remove("opacity-60", "cursor-not-allowed");
          }
        }, 2600);
      }

      function performParcelSearch() {
        if (!currentUser) {
          updateSearchAccess();
          return;
        }
        const input = document.getElementById("parcelInput");
        const raw = input ? input.value.trim() : "";
        lastParcelResult = null;
        if (!raw) {
          lastParcelResult = { notFound: true };
        } else {
          const term = raw.toUpperCase();
          const found = sampleParcels.find((p) => p.parcel_number.toUpperCase() === term);
          lastParcelResult = found || { notFound: true };
        }
        renderParcelResult();
      }

      function performTransactionSearch() {
        if (!currentUser) {
          updateSearchAccess();
          return;
        }
        const input = document.getElementById("transactionInput");
        const raw = input ? input.value.trim() : "";
        lastTransactionResult = null;
        if (!raw) {
          lastTransactionResult = { notFound: true };
        } else {
          const term = raw.toUpperCase();
          const found = sampleTransactions.find((t) => t.transaction_number.toUpperCase() === term);
          lastTransactionResult = found || { notFound: true };
        }
        renderTransactionResult();
      }

      function handleSignIn(event) {
        event.preventDefault();
        const tAcc = translations[currentLang].accounts;
        const usernameInput = document.getElementById("signInUsername");
        const passwordInput = document.getElementById("signInPassword");
        const errorEl = document.getElementById("signInError");
        const username = usernameInput ? usernameInput.value.trim() : "";
        const password = passwordInput ? passwordInput.value : "";

        const account = accounts.find((a) => a.username === username && a.password === password);
        if (!account) {
          if (errorEl) errorEl.textContent = tAcc.invalidCredentials;
          return;
        }
        if (errorEl) errorEl.textContent = "";
        currentUser = { ...account };
        saveCurrentUser();
        updateAuthUI();
      }

      function handleSignOut() {
        currentUser = null;
        saveCurrentUser();
        updateAuthUI();
      }

      function handleSignUp(event) {
        event.preventDefault();
        const tAcc = translations[currentLang].accounts;
        const usernameInput = document.getElementById("signUpUsername");
        const passwordInput = document.getElementById("signUpPassword");
        const emailInput = document.getElementById("signUpEmail");
        const phoneInput = document.getElementById("signUpPhone");
        const userTypeSelect = document.getElementById("signUpUserType");
        const orgInput = document.getElementById("signUpOrg");
        const ministryWorkerInput = document.getElementById("signUpMinistryWorker");
        const humanCheckInput = document.getElementById("signUpHumanCheck");
        const verifyMethodInputs = document.querySelectorAll('input[name="signUpVerifyMethod"]');
        const errorEl = document.getElementById("signUpError");

        const username = usernameInput ? usernameInput.value.trim() : "";
        const password = passwordInput ? passwordInput.value : "";
        const email = emailInput ? emailInput.value.trim() : "";
        const phone = phoneInput ? phoneInput.value.trim() : "";
        const userType = userTypeSelect ? userTypeSelect.value : "INDIVIDUAL";
        const org = orgInput ? orgInput.value.trim() : "";
        const isMinistryWorker = ministryWorkerInput ? ministryWorkerInput.checked : false;
        const verifyMethodNode = Array.from(verifyMethodInputs || []).find((n) => n.checked);
        const verifyMethod = verifyMethodNode ? verifyMethodNode.value : "email";

        if (!username) {
          if (errorEl) errorEl.textContent = tAcc.usernameRequired;
          return;
        }
        if (!password) {
          if (errorEl) errorEl.textContent = tAcc.passwordRequired;
          return;
        }
        if (!email) {
          if (errorEl) errorEl.textContent = tAcc.emailRequired;
          return;
        }
        if (!phone) {
          if (errorEl) errorEl.textContent = tAcc.phoneRequired;
          return;
        }
        if (!phone.startsWith("+224")) {
          if (errorEl) errorEl.textContent = tAcc.phoneRequired;
          return;
        }
        if (!humanCheckInput || !humanCheckInput.checked) {
          if (errorEl) errorEl.textContent = tAcc.humanCheckRequired;
          return;
        }
        if (accounts.some((a) => a.username === username)) {
          if (errorEl) errorEl.textContent = tAcc.usernameTaken;
          return;
        }

        const newAccount = {
          username,
          password,
          email,
          phone,
          user_type: userType,
          organization_name: org,
          is_ministry_worker: isMinistryWorker,
          role: "USER",
          is_verified: false,
          verify_method: verifyMethod
        };
        accounts.push(newAccount);
        saveAccounts();
        if (errorEl) errorEl.textContent = "";
        currentUser = { ...newAccount };
        saveCurrentUser();
        updateAuthUI();

        // Demo-only message for verification
        const tCommonLang = translations[currentLang].accounts;
        if (errorEl) {
          if (verifyMethod === "email") {
            errorEl.textContent = currentLang === "fr"
              ? "Un lien de vérification aurait été envoyé à votre adresse email dans un environnement de production."
              : "A verification link would be sent to your email address in a production environment.";
          } else {
            errorEl.textContent = currentLang === "fr"
              ? "Un code de vérification par SMS aurait été envoyé à votre téléphone dans un environnement de production."
              : "An SMS verification code would be sent to your phone in a production environment.";
          }
        }
      }

      function switchLanguage(lang) {
        if (currentLang === lang) return;
        currentLang = lang === "fr" ? "fr" : "en";
        document.documentElement.lang = currentLang;
        applyTranslations();
        updateLanguageButtons();
        updateAuthUI();
        renderParcelResult();
        renderTransactionResult();
        renderOrderSummary();
        renderPrefectures();
        renderPrefectureMapList();
        renderMinistryAccess();
      }

      function init() {
        loadState();
        document.documentElement.lang = currentLang;
        applyTranslations();
        updateLanguageButtons();
        renderPrefectures();
        renderPrefectureMapList();
        renderMinistryAccess();
        renderEmptyOrderSummary();
        updateAuthUI();

        const langEnBtn = document.getElementById("lang-en");
        const langFrBtn = document.getElementById("lang-fr");
        if (langEnBtn) langEnBtn.addEventListener("click", () => switchLanguage("en"));
        if (langFrBtn) langFrBtn.addEventListener("click", () => switchLanguage("fr"));

        const headerAccountBtn = document.getElementById("headerAccountBtn");
        if (headerAccountBtn) {
          headerAccountBtn.addEventListener("click", () => {
            const section = document.getElementById("accounts");
            if (section) section.scrollIntoView({ behavior: "smooth" });
          });
          headerAccountBtn.classList.remove("hidden");
        }

        // Account tabs
        const tabSignIn = document.getElementById("account-tab-signin");
        const tabSignUp = document.getElementById("account-tab-signup");
        const formSignIn = document.getElementById("signInForm");
        const formSignUp = document.getElementById("signUpForm");
        if (tabSignIn && tabSignUp && formSignIn && formSignUp) {
          tabSignIn.addEventListener("click", () => {
            formSignIn.classList.remove("hidden");
            formSignUp.classList.add("hidden");
            tabSignIn.classList.add("border-emerald-500", "text-emerald-300");
            tabSignUp.classList.remove("border-emerald-500", "text-emerald-300");
            tabSignUp.classList.add("text-slate-400");
          });
          tabSignUp.addEventListener("click", () => {
            formSignUp.classList.remove("hidden");
            formSignIn.classList.add("hidden");
            tabSignUp.classList.add("border-emerald-500", "text-emerald-300");
            tabSignIn.classList.remove("border-emerald-500", "text-emerald-300");
            tabSignIn.classList.add("text-slate-400");
          });
        }

        if (formSignIn) formSignIn.addEventListener("submit", handleSignIn);
        const signOutBtn = document.getElementById("signOutBtn");
        if (signOutBtn) signOutBtn.addEventListener("click", handleSignOut);
        if (formSignUp) formSignUp.addEventListener("submit", handleSignUp);

        const simulateVerifyBtn = document.getElementById("simulateVerifyBtn");
        if (simulateVerifyBtn) {
          simulateVerifyBtn.addEventListener("click", () => {
            if (!currentUser) return;
            const acc = accounts.find((a) => a.username === currentUser.username);
            if (acc) {
              acc.is_verified = true;
              saveAccounts();
            }
            currentUser.is_verified = true;
            saveCurrentUser();
            updateAuthUI();
          });
        }

        // Search tabs
        const parcelTab = document.getElementById("tab-parcel");
        const transactionTab = document.getElementById("tab-transaction");
        const parcelPanel = document.getElementById("parcel-search-panel");
        const transactionPanel = document.getElementById("transaction-search-panel");

        if (parcelTab && transactionTab && parcelPanel && transactionPanel) {
          parcelTab.addEventListener("click", () => {
            parcelPanel.classList.remove("hidden");
            transactionPanel.classList.add("hidden");
            parcelTab.classList.add("border-emerald-500", "text-emerald-300");
            transactionTab.classList.remove("border-emerald-500", "text-emerald-300");
            transactionTab.classList.add("text-slate-400");
          });
          transactionTab.addEventListener("click", () => {
            transactionPanel.classList.remove("hidden");
            parcelPanel.classList.add("hidden");
            transactionTab.classList.add("border-emerald-500", "text-emerald-300");
            parcelTab.classList.remove("border-emerald-500", "text-emerald-300");
            parcelTab.classList.add("text-slate-400");
          });
        }

        const parcelSearchBtn = document.getElementById("parcelSearchBtn");
        const txSearchBtn = document.getElementById("transactionSearchBtn");
        if (parcelSearchBtn) parcelSearchBtn.addEventListener("click", performParcelSearch);
        if (txSearchBtn) txSearchBtn.addEventListener("click", performTransactionSearch);

        const parcelInput = document.getElementById("parcelInput");
        const txInput = document.getElementById("transactionInput");
        if (parcelInput) {
          parcelInput.addEventListener("keydown", (e) => {
            if (e.key === "Enter") {
              e.preventDefault();
              performParcelSearch();
            }
          });
        }
        if (txInput) {
          txInput.addEventListener("keydown", (e) => {
            if (e.key === "Enter") {
              e.preventDefault();
              performTransactionSearch();
            }
          });
        }

        // Products
        const productFullBtn = document.getElementById("product-full");
        const productCertBtn = document.getElementById("product-cert");
        if (productFullBtn) {
          productFullBtn.addEventListener("click", () => selectProduct("FULL_PROPERTY_REPORT"));
        }
        if (productCertBtn) {
          productCertBtn.addEventListener("click", () => selectProduct("CERT_EXTRACT"));
        }
        selectProduct(selectedProductCode);

        const createOrderBtn = document.getElementById("createOrderBtn");
        if (createOrderBtn) {
          createOrderBtn.addEventListener("click", () => {
            createDemoOrder();
            const reportsSection = document.getElementById("reports");
            if (reportsSection) {
              reportsSection.scrollIntoView({ behavior: "smooth", block: "center" });
            }
          });
        }

        const startPaymentBtn = document.getElementById("startPaymentBtn");
        if (startPaymentBtn) {
          startPaymentBtn.addEventListener("click", startDemoPayment);
        }

        updateSearchAccess();
      }

      document.addEventListener("DOMContentLoaded", init);
    })();
  </script>
</body>
</html>
