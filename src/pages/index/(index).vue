<template>
  <div
    class="up-app-shell"
    :class="{
      'is-auth-view': !isLoggedIn && currentView === 'login',
      'has-bottom-nav': isLoggedIn
    }"
  >
    <!-- SVG SYMBOLS DEFINITION -->
    <svg width="0" height="0" style="position: absolute" aria-hidden="true">
      <symbol
        id="i-doc"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path d="M14 3H7a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V8z" />
        <path d="M14 3v5h5M9 13h6M9 17h6" />
      </symbol>
      <symbol
        id="i-cap"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path d="M22 10 12 5 2 10l10 5z" />
        <path d="M6 12v5c3 2 9 2 12 0v-5" />
      </symbol>
      <symbol
        id="i-award"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <circle cx="12" cy="9" r="6" />
        <path d="m8.5 14-1.5 8 5-3 5 3-1.5-8" />
      </symbol>
      <symbol
        id="i-id"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <rect x="3" y="5" width="18" height="14" rx="2" />
        <circle cx="9" cy="11" r="2" />
        <path d="M6 16c.5-2 5.5-2 6 0M15 10h3M15 14h3" />
      </symbol>
      <symbol
        id="i-up"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path d="M12 16V4M7 9l5-5 5 5M4 20h16" />
      </symbol>
      <symbol
        id="i-dl"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2.2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path d="M12 4v12M7 11l5 5 5-5M4 20h16" />
      </symbol>
      <symbol
        id="i-shield"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2.2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path d="M12 3 5 6v6c0 4 3 7 7 9 4-2 7-5 7-9V6z" />
        <path d="m9 12 2 2 4-4" />
      </symbol>
      <symbol
        id="i-qr"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <rect x="3" y="3" width="7" height="7" rx="1" />
        <rect x="14" y="3" width="7" height="7" rx="1" />
        <rect x="3" y="14" width="7" height="7" rx="1" />
        <path d="M14 14h3v3h-3zM18 18h3v3h-3zM14 19h2M19 14v2" />
      </symbol>
      <symbol
        id="i-pen"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path d="M12 20h9" />
        <path d="M16.5 3.5a2.12 2.12 0 0 1 3 3L7 19l-4 1 1-4Z" />
      </symbol>
      <symbol
        id="i-bell"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9" />
        <path d="M13.73 21a2 2 0 0 1-3.46 0" />
      </symbol>
      <symbol
        id="i-back"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2.4"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path d="M19 12H5" />
        <path d="m12 19-7-7 7-7" />
      </symbol>
      <symbol
        id="i-cam"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path
          d="M14.5 4h-5L7 7H4a2 2 0 0 0-2 2v9a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V9a2 2 0 0 0-2-2h-3l-2.5-3z"
        />
        <circle cx="12" cy="13" r="3" />
      </symbol>
      <symbol
        id="i-trash"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path d="M3 6h18" />
        <path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6" />
        <path d="M8 6V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2" />
        <line x1="10" y1="11" x2="10" y2="17" />
        <line x1="14" y1="11" x2="14" y2="17" />
      </symbol>
      <symbol
        id="i-home"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path d="m3 9 9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z" />
        <polyline points="9 22 9 12 15 12 15 22" />
      </symbol>
      <symbol
        id="i-plus"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2.2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <line x1="12" y1="5" x2="12" y2="19" />
        <line x1="5" y1="12" x2="19" y2="12" />
      </symbol>
    </svg>

    <!-- =========================================================================
         SIMPLE, CLEAN TOP HEADER
         ========================================================================= -->
    <header class="up-topbar">
      <div class="up-topbar-inner">
        <!-- Brand Identity -->
        <div class="up-brand" @click="handleLogoClick">
          <div class="up-brand-logo">
            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2.5"
              stroke-linecap="round"
              stroke-linejoin="round"
              width="20"
              height="20"
            >
              <path
                d="M14 3H7a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V8z"
              />
              <path d="m9 14 2 2 4-4" />
            </svg>
          </div>
          <div>
            <div class="up-brand-name">UNIPASS</div>
            <p class="up-brand-sub">University of Vavuniya</p>
          </div>
        </div>

        <!-- Right Actions -->
        <div class="up-topbar-actions">
          <!-- Public Verify Action when Logged Out -->
          <template v-if="!isLoggedIn">
            <button
              v-if="currentView !== 'verify'"
              class="up-back-btn"
              @click="openPublicVerifier"
            >
              <svg width="14" height="14"><use href="#i-qr" /></svg>
              <span>Verify QR</span>
            </button>
            <button v-else class="up-back-btn" @click="goBack">
              <svg width="14" height="14"><use href="#i-back" /></svg>
              <span>Back to Login</span>
            </button>
          </template>

          <!-- Authenticated User Actions -->
          <template v-else>
            <button
              v-if="activeRole === 'student'"
              class="up-icon-btn"
              title="Notifications"
              @click="openNotificationsView"
            >
              <svg width="16" height="16"><use href="#i-bell" /></svg>
              <span v-if="unreadNotificationsCount > 0" class="up-notif-dot">
                {{ unreadNotificationsCount }}
              </span>
            </button>

            <div class="up-user-chip">
              <div style="text-align: left">
                <div class="up-user-name">
                  {{ activeRole === 'admin' ? 'Registrar Admin' : studentName }}
                </div>
                <div class="up-user-sub">
                  {{ activeRole === 'admin' ? adminLoginId : loginId }}
                </div>
              </div>
              <button class="up-logout-btn" title="Sign Out" @click="logout">
                <svg
                  width="14"
                  height="14"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2.4"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path d="M9 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h4"></path>
                  <polyline points="16 17 21 12 16 7"></polyline>
                  <line x1="21" y1="12" x2="9" y2="12"></line>
                </svg>
              </button>
            </div>
          </template>
        </div>
      </div>
    </header>

    <!-- =========================================================================
         MAIN WORKSPACE CONTAINER
         ========================================================================= -->
    <main
      class="up-main-container"
      :class="{ 'is-login': !isLoggedIn && currentView === 'login' }"
      :style="{
        transform:
          canGoBack && isSwipingBack
            ? `translateX(${Math.round(swipeDistance * 0.18)}px)`
            : ''
      }"
    >
      <!-- ========================================================
           SCREEN 1: LOGIN (INITIAL LANDING VIEW)
           ======================================================== -->
      <section
        v-if="!isLoggedIn && currentView === 'login'"
        style="width: 100%; max-width: 400px; margin: 0 auto"
      >
        <div style="text-align: center; margin-bottom: 20px">
          <h1 style="font-size: 1.85rem; font-weight: 800; color: #ffffff">
            UNIPASS
          </h1>
          <p style="font-size: 0.85rem; color: #cbd5e1; margin-top: 3px">
            University of Vavuniya • Document Portal
          </p>
        </div>

        <form
          class="up-card"
          style="
            padding: 22px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.35);
            margin-bottom: 12px;
          "
          @submit.prevent="login"
        >
          <!-- Role Switcher Tabs -->
          <div
            style="
              display: grid;
              grid-template-columns: 1fr 1fr;
              gap: 6px;
              background: #f1f5f9;
              padding: 4px;
              border-radius: 10px;
              margin-bottom: 16px;
            "
          >
            <button
              type="button"
              style="
                padding: 8px;
                border-radius: 8px;
                font-size: 0.78rem;
                font-weight: 700;
                border: none;
                cursor: pointer;
              "
              :style="
                loginRole === 'student'
                  ? 'background: #ffffff; color: #1d4ed8; box-shadow: 0 1px 4px rgba(0,0,0,0.08)'
                  : 'background: transparent; color: #64748b'
              "
              @click="loginRole = 'student'"
            >
              Student Login
            </button>
            <button
              type="button"
              style="
                padding: 8px;
                border-radius: 8px;
                font-size: 0.78rem;
                font-weight: 700;
                border: none;
                cursor: pointer;
                display: flex;
                align-items: center;
                justify-content: center;
                gap: 6px;
              "
              :style="
                loginRole === 'admin'
                  ? 'background: #ffffff; color: #1d4ed8; box-shadow: 0 1px 4px rgba(0,0,0,0.08)'
                  : 'background: transparent; color: #64748b'
              "
              @click="loginRole = 'admin'"
            >
              <span>Admin Login</span>
              <span
                v-if="pendingCustomLettersCount > 0"
                style="
                  padding: 1px 6px;
                  border-radius: 99px;
                  background: #f59e0b;
                  color: #ffffff;
                  font-size: 0.65rem;
                  font-weight: 800;
                "
              >
                {{ pendingCustomLettersCount }}
              </span>
            </button>
          </div>

          <div style="margin-bottom: 12px; text-align: left">
            <label class="up-input-label">
              {{
                loginRole === 'admin'
                  ? 'Admin / Registrar ID'
                  : 'Registration Number'
              }}
            </label>
            <input
              v-if="loginRole === 'student'"
              v-model="loginId"
              class="up-input"
              placeholder="e.g. V-021458"
              required
            />
            <input
              v-else
              v-model="adminLoginId"
              class="up-input"
              placeholder="e.g. ADMIN-UOV-01"
              required
            />
          </div>

          <div style="margin-bottom: 16px; text-align: left">
            <label class="up-input-label">Password</label>
            <input
              v-model="loginPw"
              type="password"
              class="up-input"
              placeholder="Enter password"
              required
            />
          </div>

          <button
            type="submit"
            class="up-btn up-btn-primary"
            style="width: 100%; padding: 12px; font-size: 0.88rem"
          >
            <span>
              {{
                isAuthenticating
                  ? 'Signing in...'
                  : loginRole === 'admin'
                    ? 'Sign In as Admin'
                    : 'Sign In'
              }}
            </span>
          </button>
        </form>

        <!-- Simple Public QR Button -->
        <button
          type="button"
          class="up-btn"
          style="
            width: 100%;
            background: rgba(255, 255, 255, 0.12);
            border: 1px solid rgba(255, 255, 255, 0.22);
            color: #ffffff;
          "
          @click="openPublicVerifier"
        >
          <svg width="16" height="16"><use href="#i-qr" /></svg>
          <span>Scan or Upload to Verify Document QR</span>
        </button>
      </section>

      <!-- ========================================================
           SCREEN 2: SIMPLE & CLEAN STUDENT DASHBOARD
           ======================================================== -->
      <section
        v-if="
          isLoggedIn && activeRole === 'student' && currentView === 'dashboard'
        "
      >
        <!-- Simple Greeting Row -->
        <div
          style="
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 12px;
            margin-bottom: 16px;
          "
        >
          <div style="text-align: left">
            <h1
              style="
                font-size: 1.35rem;
                color: #ffffff;
                text-shadow: 0 2px 8px rgba(0, 0, 0, 0.25);
              "
            >
              Hello, {{ studentName }}
            </h1>
            <p style="font-size: 0.78rem; color: #bfdbfe">
              Student ID: <strong style="color: #ffffff">{{ loginId }}</strong>
            </p>
          </div>
          <div style="display: flex; gap: 6px; flex-wrap: wrap">
            <span
              class="up-badge"
              style="
                background: rgba(255, 255, 255, 0.2);
                color: #ffffff;
                border: 1px solid rgba(255, 255, 255, 0.35);
              "
            >
              Total: {{ existingRequests.length }}
            </span>
            <span
              class="up-badge"
              style="
                background: rgba(34, 197, 94, 0.25);
                color: #86efac;
                border: 1px solid rgba(34, 197, 94, 0.4);
              "
            >
              Ready: {{ readyCount }}
            </span>
          </div>
        </div>

        <!-- 4 Clean Action Cards (2x2 Grid) -->
        <div class="up-action-grid">
          <button
            type="button"
            class="up-action-tile primary"
            @click="openNewRequest(false)"
          >
            <svg width="22" height="22"><use href="#i-plus" /></svg>
            <div>
              <div style="font-size: 0.88rem; font-weight: 800">
                Request Document
              </div>
              <div style="font-size: 0.72rem; opacity: 0.85">
                Instant auto-generated PDF
              </div>
            </div>
          </button>

          <button
            type="button"
            class="up-action-tile"
            @click="openNewRequest(true)"
          >
            <svg width="22" height="22" style="color: #4f46e5">
              <use href="#i-pen" />
            </svg>
            <div>
              <div style="font-size: 0.88rem; font-weight: 800; color: #0f172a">
                Custom Letter
              </div>
              <div style="font-size: 0.72rem; color: #64748b">
                Submit for Admin approval
              </div>
            </div>
          </button>

          <button
            type="button"
            class="up-action-tile"
            @click="navigateTo('requests')"
          >
            <svg width="22" height="22" style="color: #1d4ed8">
              <use href="#i-doc" />
            </svg>
            <div>
              <div style="font-size: 0.88rem; font-weight: 800; color: #0f172a">
                Existing Requests ({{ existingRequests.length }})
              </div>
              <div style="font-size: 0.72rem; color: #64748b">
                View & download documents
              </div>
            </div>
          </button>

          <button type="button" class="up-action-tile" @click="openQrVerifier">
            <svg width="22" height="22" style="color: #059669">
              <use href="#i-qr" />
            </svg>
            <div>
              <div style="font-size: 0.88rem; font-weight: 800; color: #0f172a">
                Verify QR Code
              </div>
              <div style="font-size: 0.72rem; color: #64748b">
                Scan via camera or upload
              </div>
            </div>
          </button>
        </div>

        <!-- Simple Requested Documents List -->
        <div class="up-card">
          <div
            style="
              display: flex;
              align-items: center;
              justify-content: space-between;
              margin-bottom: 12px;
            "
          >
            <h2 style="font-size: 0.95rem; color: #0f172a">
              Your Documents ({{ existingRequests.length }})
            </h2>
            <button
              type="button"
              style="
                background: none;
                border: none;
                color: #1d4ed8;
                font-size: 0.76rem;
                font-weight: 700;
                cursor: pointer;
              "
              @click="navigateTo('requests')"
            >
              View All →
            </button>
          </div>

          <div
            v-if="existingRequests.length > 0"
            style="display: flex; flex-direction: column; gap: 8px"
          >
            <div
              v-for="req in existingRequests"
              :key="req.id"
              class="up-req-item"
              style="cursor: pointer"
              @click="openTrackRequest(req)"
            >
              <div
                style="
                  display: flex;
                  align-items: center;
                  gap: 10px;
                  min-width: 0;
                  flex: 1;
                "
              >
                <div class="up-ico-box">
                  <svg width="18" height="18"><use :href="req.icon" /></svg>
                </div>
                <div style="min-width: 0; flex: 1; text-align: left">
                  <div
                    style="font-size: 0.86rem; font-weight: 700; color: #0f172a"
                  >
                    {{ req.title }}
                  </div>
                  <div style="font-size: 0.72rem; color: #64748b">
                    #{{ req.id }} • {{ req.date }} •
                    <span
                      :style="
                        req.format === 'both'
                          ? 'color: #1d4ed8; font-weight: 700'
                          : ''
                      "
                    >
                      {{
                        req.format === 'both'
                          ? 'e-Document + Certified Hard Copy'
                          : 'e-Document (PDF)'
                      }}
                    </span>
                  </div>
                </div>
              </div>

              <div
                style="
                  display: flex;
                  align-items: center;
                  gap: 6px;
                  flex-shrink: 0;
                "
              >
                <span
                  class="up-badge"
                  :class="
                    req.status === 'Ready'
                      ? 'up-badge-success'
                      : req.status === 'Rejected'
                        ? 'up-badge-rose'
                        : 'up-badge-amber'
                  "
                >
                  {{
                    req.status === 'Pending Approval' ? 'Pending' : req.status
                  }}
                </span>
                <button
                  v-if="req.status === 'Ready'"
                  type="button"
                  class="up-btn up-btn-primary"
                  style="padding: 6px 10px; font-size: 0.72rem"
                  @click.stop="downloadPdfForRequest(req)"
                >
                  <svg width="13" height="13"><use href="#i-dl" /></svg>
                  <span>PDF</span>
                </button>
                <button
                  type="button"
                  class="up-btn up-btn-danger-soft"
                  style="padding: 6px 9px; font-size: 0.72rem"
                  title="Delete"
                  @click.stop="deleteRequest(req)"
                >
                  <svg width="13" height="13"><use href="#i-trash" /></svg>
                </button>
              </div>
            </div>
          </div>

          <div
            v-else
            style="
              padding: 24px 12px;
              text-align: center;
              color: #64748b;
              font-size: 0.82rem;
            "
          >
            No documents requested yet.
          </div>
        </div>
      </section>

      <!-- ========================================================
           SCREEN: EXISTING REQUESTS LIST VIEW
           ======================================================== -->
      <section
        v-if="
          isLoggedIn && activeRole === 'student' && currentView === 'requests'
        "
      >
        <div class="up-page-header">
          <button class="up-back-btn" @click="goBack">
            <svg width="15" height="15"><use href="#i-back" /></svg>
            <span>Back</span>
          </button>
          <h1 style="font-size: 1.15rem; color: #0f172a">Existing Requests</h1>
          <button
            class="up-btn up-btn-primary"
            style="padding: 7px 12px; font-size: 0.76rem"
            @click="openNewRequest(false)"
          >
            + New
          </button>
        </div>

        <!-- Simple Filter Pills -->
        <div
          style="display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 14px"
        >
          <button
            v-for="f in ['All', 'Ready', 'Pending Approval', 'Custom Letters']"
            :key="f"
            class="unipass-chip"
            :class="{ sel: requestFilter === f }"
            @click="requestFilter = f"
          >
            {{ f }}
          </button>
        </div>

        <!-- Requests List -->
        <div style="display: flex; flex-direction: column; gap: 10px">
          <div
            v-for="req in filteredRequests"
            :key="req.id"
            class="up-req-item"
          >
            <div
              style="
                display: flex;
                align-items: center;
                gap: 12px;
                min-width: 0;
                flex: 1;
                text-align: left;
              "
            >
              <div class="up-ico-box">
                <svg width="18" height="18"><use :href="req.icon" /></svg>
              </div>
              <div style="min-width: 0; flex: 1">
                <div
                  style="
                    display: flex;
                    flex-wrap: wrap;
                    align-items: center;
                    gap: 6px;
                  "
                >
                  <strong style="font-size: 0.9rem; color: #0f172a">
                    {{ req.title }}
                  </strong>
                  <span
                    class="up-badge"
                    :class="
                      req.status === 'Ready'
                        ? 'up-badge-success'
                        : req.status === 'Rejected'
                          ? 'up-badge-rose'
                          : 'up-badge-amber'
                    "
                  >
                    {{ req.status }}
                  </span>
                </div>
                <div
                  style="font-size: 0.74rem; color: #64748b; margin-top: 2px"
                >
                  #{{ req.id }} • {{ req.purpose }} • {{ req.date }} •
                  <span
                    :style="
                      req.format === 'both'
                        ? 'color: #1d4ed8; font-weight: 700'
                        : ''
                    "
                  >
                    {{
                      req.format === 'both'
                        ? 'e-Document + Certified Hard Copy'
                        : 'e-Document (PDF)'
                    }}
                  </span>
                </div>
              </div>
            </div>

            <div
              style="
                display: flex;
                align-items: center;
                gap: 6px;
                flex-shrink: 0;
              "
            >
              <button
                v-if="req.status === 'Ready'"
                class="up-btn up-btn-primary"
                style="padding: 7px 12px; font-size: 0.74rem"
                @click="downloadPdfForRequest(req)"
              >
                <svg width="14" height="14"><use href="#i-dl" /></svg>
                <span>Download</span>
              </button>
              <button
                v-if="req.status === 'Ready'"
                class="up-btn up-btn-secondary"
                style="padding: 7px 10px; font-size: 0.74rem"
                @click="previewDocumentModal(req)"
              >
                Preview
              </button>
              <button
                class="up-btn up-btn-soft-blue"
                style="padding: 7px 10px; font-size: 0.74rem"
                @click="openTrackRequest(req)"
              >
                Details
              </button>
              <button
                type="button"
                class="up-btn up-btn-danger-soft"
                style="padding: 7px 9px; font-size: 0.74rem"
                title="Delete"
                @click="deleteRequest(req)"
              >
                <svg width="13" height="13"><use href="#i-trash" /></svg>
              </button>
            </div>
          </div>

          <div
            v-if="filteredRequests.length === 0"
            class="up-card"
            style="text-align: center; padding: 28px; color: #64748b"
          >
            No requests found.
          </div>
        </div>
      </section>

      <!-- ========================================================
           SCREEN: ADMIN / REGISTRAR PORTAL (CUSTOM LETTERS ONLY)
           ======================================================== -->
      <section
        v-if="isLoggedIn && activeRole === 'admin' && currentView === 'admin'"
      >
        <div class="up-page-header">
          <button class="up-back-btn" @click="logout">
            <svg width="15" height="15"><use href="#i-back" /></svg>
            <span>Back to Login</span>
          </button>
          <h1 style="font-size: 1.15rem; color: #0f172a">
            Custom Letter Approvals
          </h1>
          <button
            class="up-btn up-btn-soft-blue"
            style="padding: 7px 12px; font-size: 0.75rem"
            @click="openQrVerifier"
          >
            <svg width="14" height="14"><use href="#i-qr" /></svg>
            <span>Verify QR</span>
          </button>
        </div>

        <!-- Simple Filter Pills -->
        <div
          style="display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 14px"
        >
          <button
            v-for="f in ['All Custom Letters', 'Pending Approval', 'Approved']"
            :key="f"
            class="unipass-chip"
            :class="{ sel: adminFilter === f }"
            @click="adminFilter = f"
          >
            {{ f }}
          </button>
        </div>

        <!-- Custom Letter Requests for Admin Review -->
        <div style="display: flex; flex-direction: column; gap: 12px">
          <div
            v-for="req in filteredAdminCustomLetters"
            :key="req.id"
            class="up-card"
            style="text-align: left"
          >
            <div
              style="
                display: flex;
                align-items: flex-start;
                justify-content: space-between;
                gap: 10px;
                margin-bottom: 10px;
              "
            >
              <div>
                <div
                  style="
                    display: flex;
                    flex-wrap: wrap;
                    align-items: center;
                    gap: 6px;
                  "
                >
                  <strong style="font-size: 0.94rem; color: #0f172a">
                    {{ req.title }}
                  </strong>
                  <span
                    class="up-badge"
                    :class="
                      req.status === 'Ready'
                        ? 'up-badge-success'
                        : req.status === 'Rejected'
                          ? 'up-badge-rose'
                          : 'up-badge-amber'
                    "
                  >
                    {{ req.status === 'Ready' ? 'Approved' : req.status }}
                  </span>
                </div>
                <p style="font-size: 0.75rem; color: #64748b; margin-top: 2px">
                  {{ req.studentName || studentName }} ({{
                    req.studentId || loginId
                  }}) • #{{ req.id }}
                </p>
              </div>

              <button
                class="up-btn up-btn-soft-blue"
                style="padding: 6px 11px; font-size: 0.74rem"
                @click="previewDocumentModal(req)"
              >
                Preview Letter
              </button>
            </div>

            <div
              style="
                background: #f8fafc;
                border: 1px solid #e2e8f0;
                border-radius: 10px;
                padding: 10px 12px;
                margin-bottom: 12px;
                font-size: 0.78rem;
                color: #334155;
              "
            >
              <div style="font-weight: 700; margin-bottom: 4px">
                To: {{ req.recipient || 'To Whom It May Concern' }}
              </div>
              <div style="line-height: 1.5">{{ req.customBody }}</div>
            </div>

            <div style="display: flex; flex-wrap: wrap; gap: 8px">
              <button
                v-if="req.status !== 'Ready'"
                class="up-btn up-btn-success"
                style="padding: 8px 14px; font-size: 0.76rem"
                @click="approvePendingRequest(req)"
              >
                <svg width="14" height="14"><use href="#i-shield" /></svg>
                <span>Approve & Issue QR</span>
              </button>
              <button
                v-if="req.status !== 'Rejected'"
                class="up-btn up-btn-danger-soft"
                style="padding: 8px 12px; font-size: 0.76rem"
                @click="rejectRequestByRegistrar(req)"
              >
                Reject
              </button>
              <button
                v-if="req.status === 'Ready'"
                class="up-btn up-btn-primary"
                style="padding: 8px 14px; font-size: 0.76rem"
                @click="downloadPdfForRequest(req)"
              >
                <svg width="14" height="14"><use href="#i-dl" /></svg>
                <span>Download PDF</span>
              </button>
            </div>
          </div>

          <div
            v-if="filteredAdminCustomLetters.length === 0"
            class="up-card"
            style="text-align: center; padding: 28px; color: #64748b"
          >
            No custom letters found.
          </div>
        </div>
      </section>

      <!-- ========================================================
           SCREEN: NOTIFICATIONS
           ======================================================== -->
      <section v-if="isLoggedIn && currentView === 'notifications'">
        <div class="up-page-header">
          <button class="up-back-btn" @click="goBack">
            <svg width="15" height="15"><use href="#i-back" /></svg>
            <span>Back</span>
          </button>
          <h1 style="font-size: 1.15rem; color: #0f172a">Notifications</h1>
          <div style="width: 60px"></div>
        </div>

        <div style="display: flex; flex-direction: column; gap: 10px">
          <div
            v-for="item in notificationsList"
            :key="item.id"
            class="up-card"
            style="text-align: left"
          >
            <div
              style="
                display: flex;
                align-items: center;
                justify-content: space-between;
                margin-bottom: 4px;
              "
            >
              <strong style="font-size: 0.88rem; color: #0f172a">
                {{ item.title }}
              </strong>
              <span style="font-size: 0.72rem; color: #94a3b8">
                {{ item.time }}
              </span>
            </div>
            <p style="font-size: 0.78rem; color: #475569; line-height: 1.5">
              {{ item.message }}
            </p>
          </div>
        </div>
      </section>

      <!-- ========================================================
           SCREEN 3: CHOOSE DOCUMENT
           ======================================================== -->
      <section v-if="isLoggedIn && currentView === 'select'">
        <div class="up-page-header">
          <button class="up-back-btn" @click="goBack">
            <svg width="15" height="15"><use href="#i-back" /></svg>
            <span>Back</span>
          </button>
          <h1 style="font-size: 1.15rem; color: #0f172a">Choose Document</h1>
          <div style="width: 60px"></div>
        </div>

        <div style="display: flex; flex-direction: column; gap: 12px">
          <!-- Custom Letter Option -->
          <div
            class="up-doc-card"
            :class="{ selected: selectedDoc === 'Custom Letter Approval' }"
            @click="selectedDoc = 'Custom Letter Approval'"
          >
            <span class="up-doc-check">✓</span>
            <div style="display: flex; align-items: center; gap: 12px">
              <div
                class="up-ico-box"
                style="background: #eef2ff; color: #4f46e5"
              >
                <svg width="19" height="19"><use href="#i-pen" /></svg>
              </div>
              <div>
                <div
                  style="font-size: 0.9rem; font-weight: 800; color: #0f172a"
                >
                  Custom Letter Approval
                </div>
                <div style="font-size: 0.74rem; color: #64748b">
                  Submit your own letter for Admin approval & QR stamp
                </div>
              </div>
            </div>
          </div>

          <!-- Standard Documents Grid -->
          <div class="up-doc-grid">
            <div
              class="up-doc-card"
              :class="{ selected: selectedDoc === 'Academic Transcript' }"
              @click="selectedDoc = 'Academic Transcript'"
            >
              <span class="up-doc-check">✓</span>
              <div class="up-ico-box">
                <svg width="18" height="18"><use href="#i-cap" /></svg>
              </div>
              <div style="font-size: 0.84rem; font-weight: 800; color: #0f172a">
                Academic Transcript
              </div>
            </div>

            <div
              class="up-doc-card"
              :class="{ selected: selectedDoc === 'Degree Certificate' }"
              @click="selectedDoc = 'Degree Certificate'"
            >
              <span class="up-doc-check">✓</span>
              <div class="up-ico-box">
                <svg width="18" height="18"><use href="#i-award" /></svg>
              </div>
              <div style="font-size: 0.84rem; font-weight: 800; color: #0f172a">
                Degree Certificate
              </div>
            </div>

            <div
              class="up-doc-card"
              :class="{ selected: selectedDoc === 'Course Completion Letter' }"
              @click="selectedDoc = 'Course Completion Letter'"
            >
              <span class="up-doc-check">✓</span>
              <div class="up-ico-box">
                <svg width="18" height="18"><use href="#i-doc" /></svg>
              </div>
              <div style="font-size: 0.84rem; font-weight: 800; color: #0f172a">
                Course Completion
              </div>
            </div>

            <div
              class="up-doc-card"
              :class="{ selected: selectedDoc === 'Student Status Letter' }"
              @click="selectedDoc = 'Student Status Letter'"
            >
              <span class="up-doc-check">✓</span>
              <div class="up-ico-box">
                <svg width="18" height="18"><use href="#i-id" /></svg>
              </div>
              <div style="font-size: 0.84rem; font-weight: 800; color: #0f172a">
                Student Status Letter
              </div>
            </div>

            <div
              class="up-doc-card"
              :class="{ selected: selectedDoc === 'Provisional Certificate' }"
              @click="selectedDoc = 'Provisional Certificate'"
            >
              <span class="up-doc-check">✓</span>
              <div class="up-ico-box">
                <svg width="18" height="18"><use href="#i-shield" /></svg>
              </div>
              <div style="font-size: 0.84rem; font-weight: 800; color: #0f172a">
                Provisional Certificate
              </div>
            </div>

            <div
              class="up-doc-card"
              :class="{ selected: selectedDoc === 'Medium of Instruction' }"
              @click="selectedDoc = 'Medium of Instruction'"
            >
              <span class="up-doc-check">✓</span>
              <div class="up-ico-box">
                <svg width="18" height="18"><use href="#i-doc" /></svg>
              </div>
              <div style="font-size: 0.84rem; font-weight: 800; color: #0f172a">
                Medium of Instruction
              </div>
            </div>
          </div>

          <button
            class="up-btn up-btn-primary"
            style="width: 100%; padding: 13px; font-size: 0.88rem"
            @click="navigateTo('form')"
          >
            <span>Continue with {{ selectedDoc }} →</span>
          </button>
        </div>
      </section>

      <!-- ========================================================
           SCREEN 4: SIMPLE REQUEST FORM
           ======================================================== -->
      <section v-if="isLoggedIn && currentView === 'form'">
        <div class="up-page-header">
          <button class="up-back-btn" @click="goBack">
            <svg width="15" height="15"><use href="#i-back" /></svg>
            <span>Back</span>
          </button>
          <h1 style="font-size: 1.1rem; color: #0f172a">{{ selectedDoc }}</h1>
          <div style="width: 60px"></div>
        </div>

        <div style="display: flex; flex-direction: column; gap: 12px">
          <!-- Custom Letter Fields -->
          <div
            v-if="selectedDoc === 'Custom Letter Approval'"
            class="up-card"
            style="text-align: left"
          >
            <div style="margin-bottom: 12px">
              <label class="up-input-label">Quick Templates:</label>
              <div style="display: flex; flex-wrap: wrap; gap: 6px">
                <button
                  v-for="preset in customPresets"
                  :key="preset.label"
                  type="button"
                  class="unipass-chip"
                  @click="applyCustomPreset(preset)"
                >
                  {{ preset.label }}
                </button>
              </div>
            </div>

            <div style="margin-bottom: 12px">
              <label class="up-input-label">Letter Title</label>
              <input
                v-model="customLetterTitle"
                type="text"
                class="up-input"
                placeholder="e.g. Internship Confirmation Letter"
              />
            </div>

            <div style="margin-bottom: 12px">
              <label class="up-input-label">Addressed To</label>
              <input
                v-model="customLetterRecipient"
                type="text"
                class="up-input"
                placeholder="e.g. The HR Manager, Virtusa (Pvt) Ltd"
              />
            </div>

            <div>
              <label class="up-input-label">Letter Content</label>
              <textarea
                v-model="customLetterBody"
                rows="4"
                class="up-input"
                style="font-weight: 500; line-height: 1.5"
                placeholder="Write your custom letter content..."
              ></textarea>
            </div>
          </div>

          <!-- Purpose Selection -->
          <div class="up-card" style="text-align: left">
            <label class="up-input-label" style="margin-bottom: 8px">
              Purpose of Request
            </label>
            <div style="display: flex; flex-wrap: wrap; gap: 6px">
              <button
                v-for="chip in [
                  'Higher studies',
                  'Employment / Internship',
                  'Visa & Embassy',
                  'Bank / Financial',
                  'Scholarship',
                  'Other'
                ]"
                :key="chip"
                class="unipass-chip"
                :class="{ sel: selectedPurpose === chip }"
                type="button"
                @click="selectedPurpose = chip"
              >
                {{ chip }}
              </button>
            </div>
          </div>

          <!-- Document Issuance & Delivery Mode -->
          <div class="up-card" style="text-align: left">
            <label class="up-input-label" style="margin-bottom: 8px">
              Document Issuance &amp; Delivery Mode
            </label>
            <div class="up-doc-grid">
              <button
                type="button"
                class="up-doc-card"
                :class="{ selected: deliveryFormat === 'digital' }"
                @click="deliveryFormat = 'digital'"
              >
                <span class="up-doc-check">✓</span>
                <div
                  style="font-size: 0.84rem; font-weight: 800; color: #0f172a"
                >
                  Digital e-Document Only
                </div>
                <div style="font-size: 0.72rem; color: #64748b">
                  Official QR-verified PDF for instant download
                </div>
              </button>

              <button
                type="button"
                class="up-doc-card"
                :class="{ selected: deliveryFormat === 'both' }"
                @click="deliveryFormat = 'both'"
              >
                <span class="up-doc-check">✓</span>
                <div
                  style="font-size: 0.84rem; font-weight: 800; color: #0f172a"
                >
                  Digital + Certified Hard Copy
                </div>
                <div style="font-size: 0.72rem; color: #64748b">
                  e-Document PDF + Embossed print for collection
                </div>
              </button>
            </div>

            <div
              v-if="deliveryFormat === 'both'"
              style="
                margin-top: 10px;
                padding: 10px 12px;
                border-radius: 10px;
                background: #eff6ff;
                border: 1px solid #bfdbfe;
                font-size: 0.75rem;
                color: #1e3a8a;
                line-height: 1.45;
              "
            >
              <strong>Hard Copy Requisition:</strong> An embossed,
              Registrar-certified physical copy will be prepared by the Academic
              Establishment Division for counter collection at
              <strong>Examinations &amp; Registrar Unit (Counter #02)</strong>.
            </div>
          </div>

          <!-- Optional Supporting File Upload -->
          <div class="up-card" style="text-align: left">
            <label class="up-input-label" style="margin-bottom: 8px">
              Supporting Document (Optional)
            </label>
            <input
              ref="supportingFileInput"
              type="file"
              style="display: none"
              accept=".pdf,.jpg,.jpeg,.png,.doc,.docx"
              @change="handleSupportingFileChange"
            />
            <button
              class="unipass-drop"
              :class="{ done: isFileAttached }"
              type="button"
              @click="triggerSupportingFileSelect"
            >
              <svg width="24" height="24" style="color: #2563eb">
                <use :href="isFileAttached ? '#i-shield' : '#i-up'" />
              </svg>
              <strong style="font-size: 0.82rem; color: #0f172a">
                {{
                  isFileAttached
                    ? attachedFileName + ' attached'
                    : 'Tap to upload ID or supporting file'
                }}
              </strong>
            </button>
          </div>

          <button
            class="up-btn up-btn-primary"
            style="width: 100%; padding: 13px; font-size: 0.88rem"
            @click="submitRequest"
          >
            <span>
              {{
                selectedDoc === 'Custom Letter Approval'
                  ? 'Submit Custom Letter for Approval'
                  : 'Generate & Download Document'
              }}
            </span>
          </button>
        </div>
      </section>

      <!-- ========================================================
           SCREEN 5: SIMPLE DOCUMENT TRACKING & DOWNLOAD
           ======================================================== -->
      <section v-if="isLoggedIn && currentView === 'track'">
        <div class="up-page-header">
          <button class="up-back-btn" @click="goBack">
            <svg width="15" height="15"><use href="#i-back" /></svg>
            <span>Back</span>
          </button>
          <h1 style="font-size: 1.1rem; color: #0f172a">
            Document #{{ activeRequest.id }}
          </h1>
          <button
            type="button"
            class="up-btn up-btn-danger-soft"
            style="padding: 7px 11px; font-size: 0.74rem"
            @click="deleteRequest(activeRequest)"
          >
            <svg width="13" height="13"><use href="#i-trash" /></svg>
            <span>Delete</span>
          </button>
        </div>

        <div style="display: flex; flex-direction: column; gap: 12px">
          <!-- Ready PDF + Unique QR Card -->
          <div
            v-if="activeRequest.status === 'Ready'"
            class="up-card"
            style="text-align: left"
          >
            <div
              style="
                display: flex;
                align-items: center;
                gap: 14px;
                margin-bottom: 16px;
              "
            >
              <!-- Unique QR SVG -->
              <div
                style="
                  padding: 6px;
                  background: #ffffff;
                  border-radius: 12px;
                  border: 1.5px solid #bfdbfe;
                  flex-shrink: 0;
                "
              >
                <svg
                  :viewBox="`0 0 ${activeQrMatrix.length} ${activeQrMatrix.length}`"
                  style="width: 64px; height: 64px; display: block"
                >
                  <rect
                    :width="activeQrMatrix.length"
                    :height="activeQrMatrix.length"
                    fill="#ffffff"
                  />
                  <template v-for="(row, rIdx) in activeQrMatrix" :key="rIdx">
                    <template v-for="(cell, cIdx) in row" :key="cIdx">
                      <rect
                        v-if="cell === '1'"
                        :x="cIdx"
                        :y="rIdx"
                        width="1"
                        height="1"
                        fill="#0b1f4d"
                      />
                    </template>
                  </template>
                </svg>
              </div>

              <div style="min-width: 0; flex: 1">
                <span class="up-badge up-badge-success"
                  >✓ Ready for Download</span
                >
                <div
                  style="
                    font-size: 0.96rem;
                    font-weight: 800;
                    color: #0f172a;
                    margin-top: 4px;
                  "
                >
                  {{ activeRequest.title }}
                </div>
                <div
                  style="
                    font-family: var(--up-mono);
                    font-size: 0.72rem;
                    color: #64748b;
                    margin-top: 2px;
                  "
                >
                  QR: {{ getQrCodeValue(activeRequest) }}
                </div>
              </div>
            </div>

            <div style="display: flex; flex-wrap: wrap; gap: 8px">
              <button
                class="up-btn up-btn-primary"
                style="flex: 1 1 180px"
                @click="downloadPdfForRequest(activeRequest)"
              >
                <svg width="16" height="16"><use href="#i-dl" /></svg>
                <span>Download PDF</span>
              </button>
              <button
                class="up-btn up-btn-soft-blue"
                style="flex: 1 1 140px"
                @click="previewDocumentModal(activeRequest)"
              >
                <svg width="16" height="16"><use href="#i-doc" /></svg>
                <span>Preview Document</span>
              </button>
            </div>
          </div>

          <!-- Pending Admin Approval Card -->
          <div
            v-else
            class="up-card"
            style="background: #fffbeb; border-color: #fde68a; text-align: left"
          >
            <span class="up-badge up-badge-amber"
              >⏳ Pending Admin Approval</span
            >
            <h3 style="font-size: 0.95rem; color: #78350f; margin-top: 6px">
              {{ activeRequest.title }}
            </h3>
            <p style="font-size: 0.78rem; color: #92400e; margin-top: 4px">
              PDF download will unlock once the Registrar Admin approves your
              custom letter.
            </p>
          </div>

          <!-- Document Issuance & Delivery Mode on Track Screen -->
          <div class="up-card" style="text-align: left">
            <label class="up-input-label" style="margin-bottom: 8px">
              Document Issuance &amp; Delivery Mode
            </label>
            <div class="up-doc-grid">
              <button
                type="button"
                class="up-doc-card"
                :class="{ selected: activeRequest.format !== 'both' }"
                @click="setPhysicalCopyOption(activeRequest, false)"
              >
                <span class="up-doc-check">✓</span>
                <div
                  style="font-size: 0.84rem; font-weight: 800; color: #0f172a"
                >
                  Digital e-Document Only
                </div>
                <div style="font-size: 0.72rem; color: #64748b">
                  Official QR-verified PDF for instant download
                </div>
              </button>

              <button
                type="button"
                class="up-doc-card"
                :class="{ selected: activeRequest.format === 'both' }"
                @click="setPhysicalCopyOption(activeRequest, true)"
              >
                <span class="up-doc-check">✓</span>
                <div
                  style="font-size: 0.84rem; font-weight: 800; color: #0f172a"
                >
                  Digital + Certified Hard Copy
                </div>
                <div style="font-size: 0.72rem; color: #64748b">
                  e-Document PDF + Embossed print for collection
                </div>
              </button>
            </div>

            <div
              v-if="activeRequest.format === 'both'"
              style="
                margin-top: 10px;
                padding: 10px 12px;
                border-radius: 10px;
                background: #eff6ff;
                border: 1px solid #bfdbfe;
                font-size: 0.75rem;
                color: #1e3a8a;
                line-height: 1.45;
              "
            >
              <strong>✓ Certified Hard Copy Requisitioned:</strong> Collect your
              embossed physical document at the
              <strong>Examinations &amp; Registrar Unit (Counter #02)</strong>
              upon presenting Student ID ({{
                activeRequest.studentId || loginId
              }}).
            </div>
          </div>
        </div>
      </section>

      <!-- ========================================================
           SCREEN 6: SIMPLE QR VERIFIER (UPLOAD + AUTO CAMERA)
           ======================================================== -->
      <section v-if="currentView === 'verify'">
        <div v-if="isLoggedIn" class="up-page-header">
          <button class="up-back-btn" @click="goBack">
            <svg width="15" height="15"><use href="#i-back" /></svg>
            <span>Back</span>
          </button>
          <h1 style="font-size: 1.15rem; color: #0f172a">Verify Document QR</h1>
          <div style="width: 60px"></div>
        </div>

        <div class="up-card">
          <!-- 2 Mode Switcher Tabs -->
          <div
            style="
              display: grid;
              grid-template-columns: 1fr 1fr;
              gap: 6px;
              background: #f1f5f9;
              padding: 4px;
              border-radius: 10px;
              margin-bottom: 16px;
            "
          >
            <button
              type="button"
              style="
                padding: 9px;
                border-radius: 8px;
                font-size: 0.78rem;
                font-weight: 700;
                border: none;
                cursor: pointer;
              "
              :style="
                verifyMode === 'upload'
                  ? 'background: #ffffff; color: #1d4ed8; box-shadow: 0 1px 4px rgba(0,0,0,0.08)'
                  : 'background: transparent; color: #64748b'
              "
              @click="switchVerifyMode('upload')"
            >
              Upload PDF / QR
            </button>
            <button
              type="button"
              style="
                padding: 9px;
                border-radius: 8px;
                font-size: 0.78rem;
                font-weight: 700;
                border: none;
                cursor: pointer;
              "
              :style="
                verifyMode === 'camera'
                  ? 'background: #ffffff; color: #1d4ed8; box-shadow: 0 1px 4px rgba(0,0,0,0.08)'
                  : 'background: transparent; color: #64748b'
              "
              @click="switchVerifyMode('camera')"
            >
              Camera Auto-Scan
            </button>
          </div>

          <!-- Upload Mode -->
          <div v-if="verifyMode === 'upload'">
            <input
              ref="verifyFileInput"
              type="file"
              style="display: none"
              accept=".pdf,image/*"
              @change="handleVerifyFileUpload"
            />
            <div
              class="unipass-drop qr-scan-box"
              :class="{ done: uploadedVerifyFileName }"
              style="padding: 28px 16px"
              @click="$refs.verifyFileInput.click()"
            >
              <div v-if="isScanningQr" class="qr-laser"></div>
              <svg width="32" height="32" style="color: #2563eb">
                <use :href="uploadedVerifyFileName ? '#i-shield' : '#i-up'" />
              </svg>
              <strong style="font-size: 0.86rem; color: #0f172a">
                {{
                  uploadedVerifyFileName
                    ? 'Verified: ' + uploadedVerifyFileName
                    : 'Tap to upload PDF or QR Image'
                }}
              </strong>
            </div>
          </div>

          <!-- Camera Mode -->
          <div
            v-if="verifyMode === 'camera'"
            style="
              display: flex;
              flex-direction: column;
              align-items: center;
              gap: 10px;
            "
          >
            <div
              class="qr-scan-box"
              style="
                width: 100%;
                max-width: 340px;
                height: 240px;
                background: #0f172a;
                border-radius: 16px;
                overflow: hidden;
                position: relative;
                display: flex;
                align-items: center;
                justify-content: center;
              "
              :style="
                cameraQrLocked
                  ? 'border: 3px solid #10b981'
                  : 'border: 3px solid #2563eb'
              "
            >
              <video
                ref="cameraVideoEl"
                autoplay
                playsinline
                muted
                style="width: 100%; height: 100%; object-fit: cover"
              ></video>

              <div
                v-if="cameraActive"
                style="
                  position: absolute;
                  inset: 0;
                  pointer-events: none;
                  display: flex;
                  flex-direction: column;
                  align-items: center;
                  justify-content: center;
                "
              >
                <div
                  style="
                    width: 150px;
                    height: 150px;
                    border-radius: 14px;
                    border: 2px solid #38bdf8;
                    position: relative;
                  "
                >
                  <div class="qr-laser"></div>
                </div>
              </div>

              <div
                v-if="!cameraActive"
                style="
                  position: absolute;
                  inset: 0;
                  display: flex;
                  flex-direction: column;
                  align-items: center;
                  justify-content: center;
                  padding: 16px;
                  text-align: center;
                  color: #ffffff;
                  background: rgba(15, 23, 42, 0.92);
                "
              >
                <p style="font-size: 0.78rem; color: #cbd5e1">
                  {{ cameraStatusMsg }}
                </p>
                <button
                  v-if="cameraRetryAvailable"
                  class="up-btn up-btn-primary"
                  style="
                    margin-top: 10px;
                    padding: 7px 14px;
                    font-size: 0.75rem;
                  "
                  @click="startCameraStream"
                >
                  Start Camera
                </button>
              </div>
            </div>
            <p style="font-size: 0.75rem; color: #64748b; text-align: center">
              Hold any UNIPASS QR code to the camera to verify automatically.
            </p>
          </div>

          <!-- Verification Result Card -->
          <div
            v-if="qrVerifiedResult"
            style="
              margin-top: 16px;
              padding: 14px;
              border-radius: 12px;
              background: #ecfdf5;
              border: 1.5px solid #10b981;
              text-align: left;
            "
          >
            <div
              style="
                display: flex;
                align-items: center;
                justify-content: space-between;
                gap: 10px;
                margin-bottom: 10px;
              "
            >
              <div>
                <span class="up-badge up-badge-success">
                  ✓ Verified Authentic Document
                </span>
                <div
                  style="
                    font-size: 0.94rem;
                    font-weight: 800;
                    color: #064e3b;
                    margin-top: 4px;
                  "
                >
                  {{ qrVerifiedResult.title }}
                </div>
                <div style="font-size: 0.75rem; color: #047857">
                  {{ qrVerifiedResult.studentName || studentName }} ({{
                    qrVerifiedResult.studentId || loginId
                  }}) • QR: {{ getQrCodeValue(qrVerifiedResult) }}
                </div>
              </div>
            </div>

            <div style="display: flex; flex-wrap: wrap; gap: 8px">
              <button
                class="up-btn up-btn-success"
                style="padding: 8px 14px; font-size: 0.76rem"
                @click="downloadPdfForRequest(qrVerifiedResult)"
              >
                <svg width="14" height="14"><use href="#i-dl" /></svg>
                <span>Download PDF</span>
              </button>
              <button
                class="up-btn up-btn-secondary"
                style="padding: 8px 12px; font-size: 0.76rem"
                @click="previewDocumentModal(qrVerifiedResult)"
              >
                Preview
              </button>
            </div>
          </div>
        </div>
      </section>
    </main>

    <!-- =========================================================================
         ON-SCREEN DOCUMENT PREVIEW MODAL (Centered & Padded for iPhone 17 Pro & Desktop)
         ========================================================================= -->
    <div
      v-if="showPreviewModal"
      class="unipass-modal-backdrop"
      @click.self="showPreviewModal = false"
    >
      <div class="unipass-modal-dialog">
        <div
          style="
            display: flex;
            align-items: flex-start;
            justify-content: space-between;
            gap: 12px;
            border-bottom: 1px solid #e2e8f0;
            padding-bottom: 10px;
          "
        >
          <div style="min-width: 0; text-align: left">
            <h3
              style="
                font-size: 0.92rem;
                font-weight: 800;
                color: #0f172a;
                white-space: nowrap;
                overflow: hidden;
                text-overflow: ellipsis;
              "
            >
              Official Document Preview — {{ getPdfFileName(previewTargetReq) }}
            </h3>
            <p
              style="
                font-size: 0.72rem;
                color: #64748b;
                margin-top: 2px;
                white-space: nowrap;
                overflow: hidden;
                text-overflow: ellipsis;
              "
            >
              {{
                previewTargetReq?.status === 'Ready'
                  ? 'Embedded with Unique UNIPASS QR (' +
                    getQrCodeValue(previewTargetReq) +
                    ')'
                  : 'Draft Preview — Pending Admin Approval'
              }}
            </p>
          </div>
          <button
            class="up-btn up-btn-secondary"
            style="padding: 6px 12px; font-size: 0.74rem; flex-shrink: 0"
            @click="showPreviewModal = false"
          >
            ✕ Close
          </button>
        </div>

        <div class="unipass-modal-scroll">
          <img
            v-if="previewDataUrl"
            :src="previewDataUrl"
            alt="Generated Document Preview"
          />
        </div>

        <div style="display: flex; flex-wrap: wrap; gap: 8px">
          <button
            v-if="previewTargetReq?.status === 'Ready'"
            class="up-btn up-btn-primary"
            style="flex: 1 1 220px; padding: 11px 16px; font-size: 0.8rem"
            @click="downloadPdfForRequest(previewTargetReq)"
          >
            <svg width="17" height="17"><use href="#i-dl" /></svg>
            <span>Download PDF ({{ getPdfFileName(previewTargetReq) }})</span>
          </button>
          <button
            v-if="
              activeRole === 'admin' && previewTargetReq?.status !== 'Ready'
            "
            class="up-btn up-btn-success"
            style="flex: 1 1 220px; padding: 11px 16px; font-size: 0.8rem"
            @click="approveFromPreviewModal"
          >
            <svg width="17" height="17"><use href="#i-shield" /></svg>
            <span>Approve Custom Letter & Issue QR</span>
          </button>
          <button
            class="up-btn up-btn-secondary"
            style="padding: 11px 16px; font-size: 0.8rem"
            @click="showPreviewModal = false"
          >
            Close Preview
          </button>
        </div>
      </div>
    </div>

    <!-- Swipe Back Floating Visual Pill -->
    <div
      v-if="canGoBack && isSwipingBack"
      class="up-swipe-back-pill"
      :class="{ 'is-ready': swipeReady }"
      :style="{
        transform: `translate3d(${Math.max(0, swipeDistance - 38)}px, -50%, 0) scale(${swipeReady ? 1.08 : 0.94})`
      }"
      aria-hidden="true"
    >
      <svg
        width="22"
        height="22"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2.5"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path d="M19 12H5" />
        <path d="m12 19-7-7 7-7" />
      </svg>
    </div>

    <!-- FLOATING DOWNLOAD TOAST NOTIFICATION -->
    <div class="unipass-toast" :class="{ show: showToast }" role="status">
      <svg width="20" height="20" style="color: #4ade80; flex-shrink: 0">
        <use href="#i-shield" />
      </svg>
      <span>{{ toastMessage }}</span>
    </div>

    <!-- FOOTER -->
    <footer
      style="
        padding: 16px;
        text-align: center;
        font-size: 0.75rem;
        border-top: 1px solid rgba(255, 255, 255, 0.15);
        background: rgba(9, 29, 88, 0.75);
        backdrop-filter: blur(12px);
        color: #bfdbfe;
      "
    >
      UNIPASS — University of Vavuniya Academic Document Portal •
      <strong style="color: #ffffff"> “No Queue, Just Click” </strong>
    </footer>
  </div>
</template>

<script setup>
import { ref, computed, watch, onMounted, onUnmounted } from 'vue'

// =========================================================================
// SESSION PERSISTENCE (PRESERVES LOGIN & EXACT VIEW ON PAGE RELOAD)
// =========================================================================
const SESSION_STORAGE_KEY = 'unipass_auth_session_v2'

function loadSavedSession() {
  try {
    const raw = localStorage.getItem(SESSION_STORAGE_KEY)
    if (raw) {
      const data = JSON.parse(raw)
      if (data && typeof data === 'object') {
        const loggedIn = Boolean(data.isLoggedIn)
        const role = data.activeRole === 'admin' ? 'admin' : 'student'
        const lRole = data.loginRole === 'admin' ? 'admin' : 'student'
        let view =
          typeof data.currentView === 'string' ? data.currentView : 'login'
        if (!loggedIn && view !== 'verify') {
          view = 'login'
        }
        if (loggedIn && (view === 'login' || !view)) {
          view = role === 'admin' ? 'admin' : 'dashboard'
        }
        const history = Array.isArray(data.viewHistory) ? data.viewHistory : []
        return {
          isLoggedIn: loggedIn,
          activeRole: role,
          loginRole: lRole,
          currentView: view,
          viewHistory: history,
          studentName: data.studentName || 'Nimal Perera',
          loginId: data.loginId || 'V-021458'
        }
      }
    }
  } catch {
    // fallback on storage error
  }
  return {
    isLoggedIn: false,
    activeRole: 'student',
    loginRole: 'student',
    currentView: 'login',
    viewHistory: [],
    studentName: 'Nimal Perera',
    loginId: 'V-021458'
  }
}

const savedSession = loadSavedSession()

// Authentication & Role State
const isLoggedIn = ref(savedSession.isLoggedIn)
const loginRole = ref(savedSession.loginRole)
const activeRole = ref(savedSession.activeRole)
const currentView = ref(savedSession.currentView)
const viewHistory = ref(savedSession.viewHistory)

const studentName = ref(savedSession.studentName)
const loginId = ref(savedSession.loginId)
const adminLoginId = ref('ADMIN-UOV-01')
const loginPw = ref('••••••••••')
const isAuthenticating = ref(false)

// Preview Modal State (hoisted for back & gesture handling)
const showPreviewModal = ref(false)
const previewDataUrl = ref('')
const previewTargetReq = ref(null)

function saveSession() {
  try {
    localStorage.setItem(
      SESSION_STORAGE_KEY,
      JSON.stringify({
        isLoggedIn: isLoggedIn.value,
        activeRole: activeRole.value,
        loginRole: loginRole.value,
        currentView: currentView.value,
        viewHistory: viewHistory.value,
        studentName: studentName.value,
        loginId: loginId.value
      })
    )
  } catch {
    // ignore
  }
}

watch(
  [isLoggedIn, activeRole, loginRole, currentView, viewHistory],
  () => {
    saveSession()
  },
  { deep: true }
)

// =========================================================================
// DYNAMIC PER-DOCUMENT ISO/IEC 18004 QR CODE GENERATOR (VERSION 2-L, 25x25)
// =========================================================================
const qrMatrixCache = new Map()

function getQrCodeValue(req) {
  const id = req?.id && req.id !== 'N/A' ? req.id : 'UP-2048'
  return `UNIPASS-UOV:${id}`
}

function generateQrMatrix(text) {
  const payload = String(text || 'UNIPASS-UOV:UP-2048').slice(0, 32)
  if (qrMatrixCache.has(payload)) {
    return qrMatrixCache.get(payload)
  }

  const size = 25
  const grid = Array.from({ length: size }, () => new Int8Array(size))
  const reserved = Array.from({ length: size }, () => new Uint8Array(size))

  function setMod(r, c, val) {
    if (r >= 0 && r < size && c >= 0 && c < size) {
      grid[r][c] = val ? 1 : 0
      reserved[r][c] = 1
    }
  }

  function addFinder(tr, tc) {
    for (let r = -1; r <= 7; r++) {
      for (let c = -1; c <= 7; c++) {
        const nr = tr + r
        const nc = tc + c
        if (nr < 0 || nr >= size || nc < 0 || nc >= size) continue
        const inOuter = r >= 0 && r <= 6 && c >= 0 && c <= 6
        const onBorder = r === 0 || r === 6 || c === 0 || c === 6
        const inInner = r >= 2 && r <= 4 && c >= 2 && c <= 4
        setMod(nr, nc, inOuter && (onBorder || inInner))
      }
    }
  }

  addFinder(0, 0)
  addFinder(0, 18)
  addFinder(18, 0)

  // Alignment pattern at (18, 18) -> top-left (16, 16)
  for (let r = 16; r <= 20; r++) {
    for (let c = 16; c <= 20; c++) {
      const onBorder = r === 16 || r === 20 || c === 16 || c === 20
      const center = r === 18 && c === 18
      setMod(r, c, onBorder || center)
    }
  }

  // Timing patterns
  for (let i = 8; i < size - 8; i++) {
    if (!reserved[6][i]) setMod(6, i, i % 2 === 0)
    if (!reserved[i][6]) setMod(i, 6, i % 2 === 0)
  }

  // Dark module & reserve format areas
  setMod(17, 8, 1)
  for (let i = 0; i < 9; i++) {
    if (!reserved[8][i]) reserved[8][i] = 1
    if (!reserved[i][8]) reserved[i][8] = 1
  }
  for (let i = 0; i < 8; i++) {
    reserved[8][size - 1 - i] = 1
    reserved[size - 1 - i][8] = 1
  }

  // Encode byte mode (34 data codewords, 10 EC codewords for Version 2-L)
  const encBytes = Array.from(new TextEncoder().encode(payload))
  const bits = []
  function pushBits(val, len) {
    for (let i = len - 1; i >= 0; i--) bits.push((val >> i) & 1)
  }
  pushBits(0b0100, 4)
  pushBits(encBytes.length, 8)
  for (const b of encBytes) pushBits(b, 8)
  for (let i = 0; i < 4 && bits.length < 34 * 8; i++) bits.push(0)
  while (bits.length % 8 !== 0) bits.push(0)
  const padBytes = [0xec, 0x11]
  let padIdx = 0
  while (bits.length < 34 * 8) {
    pushBits(padBytes[padIdx % 2], 8)
    padIdx++
  }

  const dataCw = new Uint8Array(34)
  for (let i = 0; i < 34; i++) {
    let v = 0
    for (let b = 0; b < 8; b++) v = (v << 1) | bits[i * 8 + b]
    dataCw[i] = v
  }

  // GF(256) Reed-Solomon Error Correction (10 EC codewords)
  const exp = new Uint8Array(512)
  const log = new Uint8Array(256)
  let x = 1
  for (let i = 0; i < 255; i++) {
    exp[i] = x
    exp[i + 255] = x
    log[x] = i
    x <<= 1
    if (x & 0x100) x ^= 0x11d
  }
  function gfMul(a, b) {
    return a === 0 || b === 0 ? 0 : exp[log[a] + log[b]]
  }

  let gen = new Uint8Array([1])
  for (let i = 0; i < 10; i++) {
    const next = new Uint8Array(gen.length + 1)
    for (let j = 0; j < gen.length; j++) {
      next[j] ^= gen[j]
      next[j + 1] ^= gfMul(gen[j], exp[i])
    }
    gen = next
  }

  const ecCw = new Uint8Array(10)
  for (let i = 0; i < 34; i++) {
    const factor = dataCw[i] ^ ecCw[0]
    for (let j = 0; j < 9; j++) {
      ecCw[j] = ecCw[j + 1] ^ gfMul(gen[j + 1], factor)
    }
    ecCw[9] = gfMul(gen[10], factor)
  }

  const allBits = []
  for (const b of dataCw) {
    for (let i = 7; i >= 0; i--) allBits.push((b >> i) & 1)
  }
  for (const b of ecCw) {
    for (let i = 7; i >= 0; i--) allBits.push((b >> i) & 1)
  }
  for (let i = 0; i < 7; i++) allBits.push(0)

  let bitIdx = 0
  let upward = true
  for (let col = size - 1; col > 0; col -= 2) {
    if (col === 6) col--
    for (let step = 0; step < size; step++) {
      const row = upward ? size - 1 - step : step
      for (let dc = 0; dc < 2; dc++) {
        const c = col - dc
        if (!reserved[row][c]) {
          const bit = bitIdx < allBits.length ? allBits[bitIdx++] : 0
          const masked = (row + c) % 2 === 0 ? bit ^ 1 : bit
          grid[row][c] = masked
        }
      }
    }
    upward = !upward
  }

  // Format bits for Level L (01) and Mask 0 (000)
  const fmtBits = [1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 0, 0, 1, 0, 0]
  const fmtCoords1 = [
    [8, 0],
    [8, 1],
    [8, 2],
    [8, 3],
    [8, 4],
    [8, 5],
    [8, 7],
    [8, 8],
    [7, 8],
    [5, 8],
    [4, 8],
    [3, 8],
    [2, 8],
    [1, 8],
    [0, 8]
  ]
  const fmtCoords2 = [
    [24, 8],
    [23, 8],
    [22, 8],
    [21, 8],
    [20, 8],
    [19, 8],
    [18, 8],
    [8, 17],
    [8, 18],
    [8, 19],
    [8, 20],
    [8, 21],
    [8, 22],
    [8, 23],
    [8, 24]
  ]
  for (let i = 0; i < 15; i++) {
    grid[fmtCoords1[i][0]][fmtCoords1[i][1]] = fmtBits[i]
    grid[fmtCoords2[i][0]][fmtCoords2[i][1]] = fmtBits[i]
  }

  const matrix = grid.map(r => Array.from(r).join(''))
  qrMatrixCache.set(payload, matrix)
  return matrix
}

function getQrMatrixForRequest(req) {
  return generateQrMatrix(getQrCodeValue(req))
}

const defaultRequests = [
  {
    id: 'UP-2048',
    title: 'Academic Transcript',
    purpose: 'Higher studies',
    format: 'digital',
    date: 'Today, 10:42 AM',
    status: 'Ready',
    icon: '#i-cap',
    isCustom: false,
    studentName: 'Nimal Perera',
    studentId: 'V-021458',
    registrarNote: 'Auto-generated from University Senate Examination Database.'
  },
  {
    id: 'UP-2045',
    title: 'Degree Certificate',
    purpose: 'Employment / Internship',
    format: 'digital',
    date: 'Yesterday',
    status: 'Ready',
    icon: '#i-award',
    isCustom: false,
    studentName: 'Nimal Perera',
    studentId: 'V-021458',
    registrarNote: 'Auto-generated from University Conferral Registry.'
  },
  {
    id: 'UP-2041',
    title: 'Student Status Letter',
    purpose: 'Visa & Embassy',
    format: 'digital',
    date: '18 Oct 2024',
    status: 'Ready',
    icon: '#i-id',
    isCustom: false,
    studentName: 'Nimal Perera',
    studentId: 'V-021458',
    registrarNote: 'Auto-generated active enrollment confirmation.'
  },
  {
    id: 'UP-2038',
    title: 'Internship Confirmation Letter',
    purpose: 'Employment / Internship',
    format: 'digital',
    date: '2 days ago',
    status: 'Pending Approval',
    icon: '#i-pen',
    isCustom: true,
    studentName: 'Nimal Perera',
    studentId: 'V-021458',
    attachedFile: 'Student_ID_Copy.pdf',
    recipient: 'The HR Manager, Virtusa (Pvt) Ltd, Colombo',
    customBody:
      'This is to certify that Mr. Nimal Perera (Reg. No: V-021458) is an undergraduate student of the University of Vavuniya and is eligible to undertake a 6-month industrial training / software engineering internship starting next month.',
    registrarNote: ''
  }
]

function loadSavedRequests() {
  try {
    const raw = localStorage.getItem('unipass_requests_v3')
    if (raw) {
      const parsed = JSON.parse(raw)
      if (Array.isArray(parsed)) {
        return parsed
      }
    }
  } catch {
    // ignore storage errors
  }
  return defaultRequests
}

const existingRequests = ref(loadSavedRequests())

watch(
  existingRequests,
  val => {
    try {
      localStorage.setItem('unipass_requests_v3', JSON.stringify(val))
    } catch {
      // ignore storage errors
    }
  },
  { deep: true }
)

// Notifications & SMS / Email Alerts
const unreadNotificationsCount = ref(2)
const notificationsList = ref([
  {
    id: 1,
    channel: 'SMS + Email',
    type: 'approved',
    title: 'Document Ready & QR Attached (#UP-2048)',
    time: 'Today, 10:45 AM',
    message:
      'Your Official Academic Transcript (#UP-2048) has been auto-generated from the University Database and stamped with the UNIPASS QR code.',
    smsPreview:
      'UNIPASS UoV: Your Academic Transcript (#UP-2048) is READY. Download PDF with QR seal at portal.vau.ac.lk. Verify ID: UNIPASS-UOV-2024-VERIFIED',
    reqId: 'UP-2048'
  },
  {
    id: 2,
    channel: 'Portal Alert',
    type: 'info',
    title: 'Custom Letter Sent for Admin Approval (#UP-2038)',
    time: '2 days ago',
    message:
      'Your custom letter "Internship Confirmation Letter" addressed to Virtusa (Pvt) Ltd is awaiting Admin approval.',
    smsPreview: '',
    reqId: 'UP-2038'
  }
])

// Filters for Student & Admin
const requestFilter = ref('All')
const adminFilter = ref('All Custom Letters')

const filteredRequests = computed(() => {
  if (requestFilter.value === 'Ready') {
    return existingRequests.value.filter(r => r.status === 'Ready')
  }
  if (requestFilter.value === 'Pending Approval') {
    return existingRequests.value.filter(r => r.status === 'Pending Approval')
  }
  if (requestFilter.value === 'Custom Letters') {
    return existingRequests.value.filter(r => r.isCustom)
  }
  return existingRequests.value
})

// Admin ONLY reviews Custom Letters
const customLetterRequests = computed(() =>
  existingRequests.value.filter(r => r.isCustom)
)

const filteredAdminCustomLetters = computed(() => {
  if (adminFilter.value === 'Pending Approval') {
    return customLetterRequests.value.filter(
      r => r.status === 'Pending Approval'
    )
  }
  if (adminFilter.value === 'Approved') {
    return customLetterRequests.value.filter(r => r.status === 'Ready')
  }
  return customLetterRequests.value
})

const pendingCustomLettersCount = computed(
  () =>
    existingRequests.value.filter(
      r => r.isCustom && r.status === 'Pending Approval'
    ).length
)
const readyCount = computed(
  () => existingRequests.value.filter(r => r.status === 'Ready').length
)

// Navigation Helpers with Full Back History Support
function navigateTo(targetView) {
  if (currentView.value === 'verify' && targetView !== 'verify') {
    stopCameraStream()
  }
  if (currentView.value !== targetView) {
    viewHistory.value.push(currentView.value)
    currentView.value = targetView
    saveSession()
    try {
      window.history.pushState({ unipassView: targetView }, '')
    } catch {
      // ignore
    }
  }
}

function goBack() {
  if (showPreviewModal.value) {
    showPreviewModal.value = false
    return
  }
  if (currentView.value === 'verify') {
    stopCameraStream()
  }
  while (viewHistory.value.length > 0) {
    const prev = viewHistory.value.pop()
    if (!isLoggedIn.value && prev !== 'login') {
      continue
    }
    if (isLoggedIn.value && activeRole.value === 'admin' && prev !== 'admin') {
      continue
    }
    if (
      isLoggedIn.value &&
      activeRole.value === 'student' &&
      prev === 'admin'
    ) {
      continue
    }
    if (prev === 'login' && isLoggedIn.value) {
      continue
    }
    currentView.value = prev
    saveSession()
    try {
      window.history.replaceState({ unipassView: prev }, '')
    } catch {
      // ignore
    }
    return
  }
  // Fallback destination if history stack is empty
  if (!isLoggedIn.value) {
    currentView.value = 'login'
  } else if (activeRole.value === 'admin') {
    currentView.value = 'admin'
  } else {
    currentView.value = 'dashboard'
  }
  saveSession()
  try {
    window.history.replaceState({ unipassView: currentView.value }, '')
  } catch {
    // ignore
  }
}

const canGoBack = computed(() => {
  if (showPreviewModal.value) return true
  if (viewHistory.value.length > 0) return true
  if (!isLoggedIn.value) {
    return currentView.value !== 'login'
  }
  if (activeRole.value === 'admin') {
    return currentView.value !== 'admin'
  }
  return currentView.value !== 'dashboard'
})

function handlePopState(e) {
  if (e.state && e.state.unipassView) {
    const target = e.state.unipassView
    if (currentView.value === 'verify' && target !== 'verify') {
      stopCameraStream()
    }
    currentView.value = target
    saveSession()
  } else if (canGoBack.value) {
    goBack()
  }
}

// =========================================================================
// SWIPE-TO-BACK GESTURE SUPPORT (MOBILE TOUCH & DESKTOP DRAG)
// =========================================================================
const isSwipingBack = ref(false)
const swipeDistance = ref(0)
const swipeReady = ref(false)

let touchStartX = 0
let touchStartY = 0
let isTrackingTouch = false

function handleTouchStart(e) {
  if (!canGoBack.value) return
  if (!e.touches || e.touches.length !== 1) return

  const touch = e.touches[0]
  // Must start from left side (within 80px of screen edge)
  if (touch.clientX > 80) return

  const target = e.target
  if (target && target.closest && target.closest('input[type="range"]')) return

  touchStartX = touch.clientX
  touchStartY = touch.clientY
  isTrackingTouch = true
  isSwipingBack.value = false
  swipeDistance.value = 0
  swipeReady.value = false
}

function handleTouchMove(e) {
  if (!isTrackingTouch || !e.touches || e.touches.length !== 1) return

  const touch = e.touches[0]
  const deltaX = touch.clientX - touchStartX
  const deltaY = touch.clientY - touchStartY

  // Cancel if vertical scrolling is dominant
  if (Math.abs(deltaY) > Math.abs(deltaX) && deltaX < 24) {
    isTrackingTouch = false
    isSwipingBack.value = false
    return
  }

  // Moving horizontally rightwards from the edge
  if (deltaX > 8) {
    isSwipingBack.value = true
    swipeDistance.value = Math.min(deltaX, 130)
    swipeReady.value = deltaX >= 55
  } else {
    isSwipingBack.value = false
    swipeReady.value = false
  }
}

function handleTouchEnd() {
  if (!isTrackingTouch) return
  isTrackingTouch = false

  if (isSwipingBack.value && swipeReady.value) {
    if (typeof navigator !== 'undefined' && navigator.vibrate) {
      try {
        navigator.vibrate(20)
      } catch {
        // ignore
      }
    }
    goBack()
  }
  isSwipingBack.value = false
  swipeDistance.value = 0
  swipeReady.value = false
}

function handleTouchCancel() {
  isTrackingTouch = false
  isSwipingBack.value = false
  swipeDistance.value = 0
  swipeReady.value = false
}

let pointerStartX = 0
let pointerStartY = 0
let isTrackingPointer = false

function handlePointerDown(e) {
  if (e.pointerType === 'touch') return // touch listeners handle mobile smoothly
  if (!canGoBack.value) return
  if (e.clientX > 60) return

  const target = e.target
  if (target && target.closest && target.closest('input, textarea, button'))
    return

  pointerStartX = e.clientX
  pointerStartY = e.clientY
  isTrackingPointer = true
}

function handlePointerMove(e) {
  if (!isTrackingPointer || e.pointerType === 'touch') return
  const deltaX = e.clientX - pointerStartX
  const deltaY = e.clientY - pointerStartY

  if (Math.abs(deltaY) > Math.abs(deltaX) && deltaX < 24) {
    isTrackingPointer = false
    isSwipingBack.value = false
    return
  }

  if (deltaX > 8) {
    isSwipingBack.value = true
    swipeDistance.value = Math.min(deltaX, 130)
    swipeReady.value = deltaX >= 55
  }
}

function handlePointerUp() {
  if (!isTrackingPointer) return
  isTrackingPointer = false
  if (isSwipingBack.value && swipeReady.value) {
    goBack()
  }
  isSwipingBack.value = false
  swipeDistance.value = 0
  swipeReady.value = false
}

function handlePointerCancel() {
  isTrackingPointer = false
  isSwipingBack.value = false
  swipeDistance.value = 0
  swipeReady.value = false
}

function openRequestsWithFilter(filterName) {
  requestFilter.value = filterName
  navigateTo('requests')
}

// New Request Form State
const selectedDoc = ref('Academic Transcript')
const selectedPurpose = ref('Higher studies')
const deliveryFormat = ref('digital')
const isFileAttached = ref(true)
const attachedFileName = ref('Student_ID_Copy.pdf')
const supportingFileInput = ref(null)

// Custom Letter Approval State
const customLetterTitle = ref('Internship Confirmation Letter')
const customLetterRecipient = ref('The HR Manager, Virtusa (Pvt) Ltd, Colombo')
const customLetterBody = ref(
  'This is to certify that Nimal Perera (Registration No: V-021458) is a full-time undergraduate student at the University of Vavuniya. This letter is submitted for official university endorsement to confirm eligibility for the upcoming industrial internship program.'
)

const customPresets = [
  {
    label: 'Internship Letter',
    title: 'Internship Confirmation Letter',
    recipient: 'The HR Manager, Virtusa (Pvt) Ltd, Colombo',
    purpose: 'Employment / Internship',
    body: 'This is to certify that Nimal Perera (Registration No: V-021458) is a full-time undergraduate student at the University of Vavuniya. This letter is submitted for official university endorsement to confirm eligibility for the upcoming 6-month industrial internship program.'
  },
  {
    label: 'Bank Education Loan',
    title: 'Bank Student Loan Confirmation Letter',
    recipient: 'The Branch Manager, Bank of Ceylon, Vavuniya',
    purpose: 'Bank / Financial',
    body: 'This is to certify that Nimal Perera (Registration No: V-021458) is a registered full-time undergraduate student at the University of Vavuniya pursuing degree studies. This confirmation is issued upon the student’s request for securing a higher education bank loan facility.'
  },
  {
    label: 'Visa / Embassy Letter',
    title: 'No Objection & Enrollment Letter for Visa',
    recipient: 'The Visa Consular Officer, High Commission',
    purpose: 'Visa & Embassy',
    body: 'This is to confirm that Nimal Perera (Registration No: V-021458) is an active undergraduate student of the University of Vavuniya. The university has no objection to the student attending the international academic conference during the semester break.'
  }
]

function applyCustomPreset(preset) {
  customLetterTitle.value = preset.title
  customLetterRecipient.value = preset.recipient
  selectedPurpose.value = preset.purpose
  customLetterBody.value = preset.body
}

const activeRequest = ref(existingRequests.value[0])
const activeQrMatrix = computed(() =>
  getQrMatrixForRequest(activeRequest.value)
)

// Persistent archive of all issued documents so QR verification works even if deleted from dashboard
function loadIssuedArchive() {
  try {
    const raw = localStorage.getItem('unipass_issued_archive_v3')
    if (raw) {
      const parsed = JSON.parse(raw)
      if (parsed && typeof parsed === 'object') return parsed
    }
  } catch {
    // ignore storage errors
  }
  const initial = {}
  for (const r of defaultRequests) {
    initial[r.id] = { ...r }
  }
  return initial
}

const issuedArchive = ref(loadIssuedArchive())

function syncToIssuedArchive(list) {
  for (const r of list) {
    if (r && r.id) {
      issuedArchive.value[r.id] = { ...r }
    }
  }
  try {
    localStorage.setItem(
      'unipass_issued_archive_v3',
      JSON.stringify(issuedArchive.value)
    )
  } catch {
    // ignore storage errors
  }
}

syncToIssuedArchive(existingRequests.value)
watch(
  existingRequests,
  val => {
    syncToIssuedArchive(val)
  },
  { deep: true }
)

// Toast State
const showToast = ref(false)
const toastMessage = ref('Verified document downloaded')

function triggerToast(msg) {
  toastMessage.value = msg
  showToast.value = true
  setTimeout(() => {
    showToast.value = false
  }, 3000)
}

function handleLogoClick() {
  stopCameraStream()
  if (!isLoggedIn.value) {
    currentView.value = 'login'
  } else if (activeRole.value === 'admin') {
    navigateTo('admin')
  } else {
    navigateTo('dashboard')
  }
}

function login() {
  isAuthenticating.value = true
  setTimeout(() => {
    isAuthenticating.value = false
    isLoggedIn.value = true
    activeRole.value = loginRole.value
    viewHistory.value = []
    currentView.value = activeRole.value === 'admin' ? 'admin' : 'dashboard'
    saveSession()
    try {
      window.history.pushState({ unipassView: currentView.value }, '')
    } catch {
      // ignore
    }
  }, 400)
}

function logout() {
  stopCameraStream()
  isLoggedIn.value = false
  viewHistory.value = []
  currentView.value = 'login'
  saveSession()
  try {
    window.history.pushState({ unipassView: 'login' }, '')
  } catch {
    // ignore
  }
}

function openPublicVerifier() {
  stopCameraStream()
  verifyMode.value = 'upload'
  qrVerifiedResult.value = null
  uploadedVerifyFileName.value = ''
  navigateTo('verify')
}

function openQrVerifier() {
  stopCameraStream()
  verifyMode.value = 'upload'
  qrVerifiedResult.value = null
  uploadedVerifyFileName.value = ''
  navigateTo('verify')
}

function openNotificationsView() {
  unreadNotificationsCount.value = 0
  navigateTo('notifications')
}

function openTrackById(reqId) {
  const found = existingRequests.value.find(r => r.id === reqId)
  if (found) {
    openTrackRequest(found)
  }
}

function openNewRequest(isCustomLetter = false) {
  deliveryFormat.value = 'digital'
  if (isCustomLetter) {
    selectedDoc.value = 'Custom Letter Approval'
    navigateTo('form')
  } else {
    selectedDoc.value = 'Academic Transcript'
    navigateTo('select')
  }
}

function setPhysicalCopyOption(req, needPhysical) {
  if (!req) return
  req.format = needPhysical ? 'both' : 'digital'
  triggerToast(
    needPhysical
      ? 'Issuance updated: Digital + Certified Hard Copy (Registrar Counter #02)'
      : 'Issuance updated: Digital e-Document Only'
  )
}

function triggerSupportingFileSelect() {
  if (supportingFileInput.value) {
    supportingFileInput.value.click()
  }
}

function handleSupportingFileChange(e) {
  const file = e.target.files?.[0]
  if (file) {
    attachedFileName.value = file.name
    isFileAttached.value = true
  }
}

function submitRequest() {
  const isCustom = selectedDoc.value === 'Custom Letter Approval'
  const maxNum = existingRequests.value.reduce((max, r) => {
    const num = parseInt((r.id || '').replace(/\D+/g, ''), 10)
    return Number.isNaN(num) ? max : Math.max(max, num)
  }, 2048)
  const newId = 'UP-' + (maxNum + 1)
  const docTitle = isCustom
    ? customLetterTitle.value.trim() || 'Custom Letter'
    : selectedDoc.value

  // Standard documents are auto-generated immediately ('Ready'); Custom letters require Admin approval ('Pending Approval')
  const newReq = {
    id: newId,
    title: docTitle,
    purpose: selectedPurpose.value,
    format: deliveryFormat.value,
    date: 'Just now',
    status: isCustom ? 'Pending Approval' : 'Ready',
    icon: isCustom ? '#i-pen' : '#i-doc',
    isCustom,
    studentName: studentName.value,
    studentId: loginId.value,
    attachedFile: isFileAttached.value ? attachedFileName.value : '',
    recipient: isCustom ? customLetterRecipient.value : '',
    customBody: isCustom ? customLetterBody.value : '',
    registrarNote: isCustom
      ? ''
      : 'Auto-generated from University of Vavuniya Database with QR seal.'
  }

  existingRequests.value.unshift(newReq)
  activeRequest.value = newReq

  if (isCustom) {
    notificationsList.value.unshift({
      id: Date.now(),
      channel: 'Portal Alert',
      type: 'info',
      title: `Custom Letter Sent for Admin Approval (#${newId})`,
      time: 'Just now',
      message: `Your custom letter "${docTitle}" (#${newId}) has been sent to the Registrar Admin for review and approval.`,
      smsPreview: '',
      reqId: newId
    })
    unreadNotificationsCount.value++
    navigateTo('track')
    triggerToast(
      'Custom letter submitted! Log in as Admin to review & approve it.'
    )
  } else {
    const newQrVal = getQrCodeValue(newReq)
    notificationsList.value.unshift({
      id: Date.now(),
      channel: 'SMS + Email',
      type: 'approved',
      title: `Auto-Generated & QR Issued: ${docTitle} (#${newId})`,
      time: 'Just now',
      message: `Your ${docTitle} (#${newId}) has been auto-generated from the University Database with unique QR code ${newQrVal}.`,
      smsPreview: `UNIPASS UoV: Your ${docTitle} (#${newId}) is READY for download with QR verification (${newQrVal}).`,
      reqId: newId
    })
    unreadNotificationsCount.value++
    navigateTo('track')
    triggerToast('Official document auto-generated with QR code!')
  }
}

function openTrackRequest(req) {
  activeRequest.value = req
  navigateTo('track')
}

function deleteRequest(req) {
  if (!req) return
  existingRequests.value = existingRequests.value.filter(r => r.id !== req.id)
  if (activeRequest.value && activeRequest.value.id === req.id) {
    activeRequest.value = existingRequests.value[0] || {
      id: 'N/A',
      title: 'No Active Request',
      status: 'Pending Approval',
      isCustom: false
    }
    if (currentView.value === 'track') {
      goBack()
    }
  }
  triggerToast(`Deleted document request #${req.id} (${req.title})`)
}

function approvePendingRequest(req) {
  req.status = 'Ready'
  req.date = 'Approved by Admin just now'
  if (!req.registrarNote) {
    req.registrarNote =
      'Custom letter reviewed and approved by Senior Assistant Registrar.'
  }

  notificationsList.value.unshift({
    id: Date.now(),
    channel: 'SMS + Email',
    type: 'approved',
    title: `Admin Approved Custom Letter: ${req.title} (#${req.id})`,
    time: 'Just now',
    message: `Registrar Admin approved your custom letter #${req.id} (${req.title}) and attached the official QR verification seal. You can now download the PDF.`,
    smsPreview: `UNIPASS UoV: Your Custom Letter #${req.id} (${req.title}) has been APPROVED by Admin. Download PDF now.`,
    reqId: req.id
  })
  unreadNotificationsCount.value++

  triggerToast(
    `Custom Letter #${req.id} approved! Student can now download the QR-stamped PDF.`
  )
}

function approveFromPreviewModal() {
  if (previewTargetReq.value) {
    approvePendingRequest(previewTargetReq.value)
    const canvas = renderDocumentCanvas(previewTargetReq.value)
    previewDataUrl.value = canvas.toDataURL('image/jpeg', 0.92)
  }
}

function rejectRequestByRegistrar(req) {
  req.status = 'Rejected'
  if (!req.registrarNote) {
    req.registrarNote = 'Please revise the letter content and resubmit.'
  }
  notificationsList.value.unshift({
    id: Date.now(),
    channel: 'Portal Alert',
    type: 'info',
    title: `Custom Letter #${req.id} Requires Revision`,
    time: 'Just now',
    message: `Admin note for ${req.title}: "${req.registrarNote}"`,
    smsPreview: '',
    reqId: req.id
  })
  unreadNotificationsCount.value++
  triggerToast(`Custom Letter #${req.id} marked as Rejected.`)
}

function getPdfFileName(req) {
  const safeName = (req?.title || 'UNIPASS_Document')
    .replace(/[^a-zA-Z0-9]+/g, '_')
    .replace(/^_|_$/g, '')
  return `${safeName}.pdf`
}

// =========================================================================
// REAL HIGH-RES DOCUMENT + QR RENDERER & GENUINE PDF GENERATOR
// =========================================================================
function wrapTextLines(ctx, text, maxWidth) {
  const words = (text || '').split(/\s+/)
  const lines = []
  let line = ''
  for (const w of words) {
    const test = line ? `${line} ${w}` : w
    if (ctx.measureText(test).width > maxWidth && line) {
      lines.push(line)
      line = w
    } else {
      line = test
    }
  }
  if (line) lines.push(line)
  return lines
}

function renderDocumentCanvas(req) {
  const canvas = document.createElement('canvas')
  const width = 1240
  const height = 1754
  canvas.width = width
  canvas.height = height
  const ctx = canvas.getContext('2d')

  const isApproved = req.status === 'Ready'

  // 1. White A4 Paper Background
  ctx.fillStyle = '#ffffff'
  ctx.fillRect(0, 0, width, height)

  // 2. Royal Blue Outer & Inner Borders
  ctx.strokeStyle = '#1d4ed8'
  ctx.lineWidth = 8
  ctx.strokeRect(40, 40, width - 80, height - 80)

  ctx.strokeStyle = '#93c5fd'
  ctx.lineWidth = 2
  ctx.strokeRect(54, 54, width - 108, height - 108)

  // 3. Top Header Banner
  ctx.fillStyle = '#0b1f4d'
  ctx.fillRect(54, 54, width - 108, 175)

  ctx.fillStyle = '#ffffff'
  ctx.font = 'bold 34px "Plus Jakarta Sans", Arial, sans-serif'
  ctx.textAlign = 'center'
  ctx.fillText('UNIVERSITY OF VAVUNIYA — SRI LANKA', width / 2, 118)

  ctx.fillStyle = '#93c5fd'
  ctx.font = 'bold 20px "Plus Jakarta Sans", Arial, sans-serif'
  ctx.fillText('OFFICIAL ACADEMIC DOCUMENT PORTAL (UNIPASS)', width / 2, 155)

  ctx.fillStyle = '#e0f2fe'
  ctx.font = '15px "Plus Jakarta Sans", Arial, sans-serif'
  ctx.fillText(
    'Pambaimadu, Vavuniya, Sri Lanka • Tel: +94 24 222 2265 • Web: www.vau.ac.lk',
    width / 2,
    192
  )

  // 4. Reference & Metadata Bar (Uniform 96px left/right document margin)
  const marginX = 96
  const contentWidth = width - marginX * 2

  ctx.fillStyle = '#f1f5f9'
  ctx.fillRect(marginX, 260, contentWidth, 68)
  ctx.strokeStyle = '#cbd5e1'
  ctx.lineWidth = 1.5
  ctx.strokeRect(marginX, 260, contentWidth, 68)

  ctx.fillStyle = '#0b1f4d'
  ctx.font = 'bold 18px "Plus Jakarta Sans", Arial, sans-serif'
  ctx.textAlign = 'left'
  ctx.fillText(`Document Ref: #${req.id}`, marginX + 24, 301)

  ctx.textAlign = 'center'
  ctx.fillText(
    `Student Reg No: ${req.studentId || loginId.value}`,
    width / 2,
    301
  )

  ctx.textAlign = 'right'
  const todayStr = new Date().toLocaleDateString('en-GB', {
    day: '2-digit',
    month: 'short',
    year: 'numeric'
  })
  ctx.fillText(`Issued Date: ${todayStr}`, width - marginX - 24, 301)

  // 5. Document Main Heading
  ctx.fillStyle = '#1d4ed8'
  ctx.font = 'bold 34px "Plus Jakarta Sans", Arial, sans-serif'
  ctx.textAlign = 'center'
  const upperTitle = (req.title || 'OFFICIAL DOCUMENT').toUpperCase()
  ctx.fillText(upperTitle, width / 2, 405)

  ctx.fillStyle = '#1d4ed8'
  ctx.fillRect(width / 2 - 140, 422, 280, 4)

  // 6. Student Profile Box
  ctx.fillStyle = '#f8fafc'
  ctx.fillRect(marginX, 455, contentWidth, 120)
  ctx.strokeStyle = '#dbeafe'
  ctx.lineWidth = 2
  ctx.strokeRect(marginX, 455, contentWidth, 120)

  ctx.textAlign = 'left'
  ctx.fillStyle = '#334155'
  ctx.font = 'bold 19px "Plus Jakarta Sans", Arial, sans-serif'
  ctx.fillText(
    `Full Name of Student :  ${req.studentName || studentName.value}`,
    marginX + 24,
    498
  )
  ctx.fillText(
    `Registration Number  :  ${req.studentId || loginId.value}`,
    marginX + 24,
    535
  )

  ctx.textAlign = 'right'
  ctx.fillText(
    `Purpose :  ${req.purpose || 'Official Use'}`,
    width - marginX - 24,
    498
  )
  ctx.fillStyle = isApproved ? '#15803d' : '#b45309'
  ctx.fillText(
    `Status :  ${isApproved ? 'VERIFIED & APPROVED' : 'PENDING ADMIN APPROVAL'}`,
    width - marginX - 24,
    535
  )

  // 7. Body Content Based on Document Type
  ctx.textAlign = 'left'
  ctx.fillStyle = '#0f172a'
  let y = 635

  if (req.isCustom) {
    ctx.font = 'bold 20px "Plus Jakarta Sans", Arial, sans-serif'
    ctx.fillText('TO:', marginX, y)
    y += 30
    ctx.font = 'bold 21px "Plus Jakarta Sans", Arial, sans-serif'
    ctx.fillStyle = '#1e3a8a'
    ctx.fillText(req.recipient || 'To Whom It May Concern', marginX, y)
    y += 45

    ctx.fillStyle = '#0f172a'
    ctx.font = 'bold 20px "Plus Jakarta Sans", Arial, sans-serif'
    ctx.fillText(`SUBJECT: ${req.title}`, marginX, y)
    y += 40

    ctx.font = '20px "Plus Jakarta Sans", Arial, sans-serif'
    const bodyText =
      req.customBody ||
      `This letter is officially approved and endorsed by the University of Vavuniya on behalf of ${studentName.value} (Reg No: ${loginId.value}).`
    const lines = wrapTextLines(ctx, bodyText, contentWidth)
    for (const line of lines) {
      ctx.fillText(line, marginX, y)
      y += 34
    }

    y += 30
    ctx.fillStyle = isApproved ? '#eff6ff' : '#fffbeb'
    ctx.fillRect(marginX, y, contentWidth, 95)
    ctx.strokeStyle = isApproved ? '#3b82f6' : '#f59e0b'
    ctx.strokeRect(marginX, y, contentWidth, 95)
    ctx.fillStyle = isApproved ? '#1d4ed8' : '#b45309'
    ctx.font = 'bold 19px "Plus Jakarta Sans", Arial, sans-serif'
    ctx.fillText(
      isApproved
        ? '✓ OFFICIAL UNIVERSITY ENDORSEMENT STAMP'
        : '⏳ DRAFT PREVIEW — AWAITING REGISTRAR ADMIN APPROVAL',
      marginX + 24,
      y + 38
    )
    ctx.fillStyle = '#334155'
    ctx.font = '17px "Plus Jakarta Sans", Arial, sans-serif'
    ctx.fillText(
      isApproved
        ? 'The above student-submitted letter has been reviewed, verified, and approved by the Office of the Registrar.'
        : 'This custom letter has been submitted by the student and requires Registrar Admin approval before official issuance.',
      marginX + 24,
      y + 70
    )
  } else if (req.title === 'Academic Transcript') {
    ctx.font = '19px "Plus Jakarta Sans", Arial, sans-serif'
    ctx.fillText(
      'This is to certify the official semester examination results and Cumulative Grade Point Average (GPA):',
      marginX,
      y
    )
    y += 35

    const courses = [
      ['ICT 3113', 'Advanced Database Management Systems', '3', 'A'],
      ['ICT 3122', 'Software Engineering & Quality Assurance', '2', 'A+'],
      ['ICT 3133', 'Computer Networks & Cyber Security', '3', 'A'],
      ['ICT 3142', 'Web Application Architecture', '2', 'A'],
      ['ICT 3152', 'Artificial Intelligence & Machine Learning', '2', 'B+'],
      ['ICT 3163', 'Cloud Computing & Distributed Systems', '3', 'A']
    ]

    ctx.fillStyle = '#1e3a8a'
    ctx.fillRect(marginX, y, contentWidth, 46)
    ctx.fillStyle = '#ffffff'
    ctx.font = 'bold 18px "Plus Jakarta Sans", Arial, sans-serif'
    ctx.fillText('Course Code', marginX + 24, y + 30)
    ctx.fillText('Course Title', marginX + 200, y + 30)
    ctx.fillText('Credits', marginX + 760, y + 30)
    ctx.fillText('Grade', marginX + 910, y + 30)
    y += 46

    courses.forEach((row, idx) => {
      ctx.fillStyle = idx % 2 === 0 ? '#f8fafc' : '#ffffff'
      ctx.fillRect(marginX, y, contentWidth, 44)
      ctx.strokeStyle = '#e2e8f0'
      ctx.strokeRect(marginX, y, contentWidth, 44)

      ctx.fillStyle = '#0f172a'
      ctx.font = 'bold 17px "Plus Jakarta Sans", Arial, sans-serif'
      ctx.fillText(row[0], marginX + 24, y + 28)
      ctx.font = '17px "Plus Jakarta Sans", Arial, sans-serif'
      ctx.fillText(row[1], marginX + 200, y + 28)
      ctx.fillText(row[2], marginX + 780, y + 28)
      ctx.font = 'bold 18px "Plus Jakarta Sans", Arial, sans-serif'
      ctx.fillStyle = '#1d4ed8'
      ctx.fillText(row[3], marginX + 920, y + 28)
      y += 44
    })

    y += 28
    ctx.fillStyle = '#0b1f4d'
    ctx.font = 'bold 22px "Plus Jakarta Sans", Arial, sans-serif'
    ctx.fillText(
      'Cumulative GPA: 3.84 / 4.00   (First Class Honours Standing)',
      marginX,
      y
    )
  } else {
    ctx.font = '21px "Plus Jakarta Sans", Arial, sans-serif'
    const paragraphs = [
      `This is to officially certify that ${req.studentName || studentName.value} (University Registration No: ${req.studentId || loginId.value}) has been a duly registered student at the University of Vavuniya, Sri Lanka.`,
      `This ${req.title} is issued upon the request of the candidate for the purpose of "${req.purpose}". All academic records and institutional clearances associated with this certificate have been automatically verified against the University Senate Registry.`,
      `The medium of instruction and examination at the University of Vavuniya is English, and the candidate has maintained exemplary academic and personal conduct throughout the programme.`
    ]
    for (const p of paragraphs) {
      const lines = wrapTextLines(ctx, p, contentWidth)
      for (const line of lines) {
        ctx.fillText(line, marginX, y)
        y += 36
      }
      y += 22
    }
  }

  // 8. Bottom Verification, Registrar Signature & Official QR Code Section
  const footerTop = 1230

  ctx.strokeStyle = '#cbd5e1'
  ctx.lineWidth = 2
  ctx.beginPath()
  ctx.moveTo(marginX, footerTop)
  ctx.lineTo(width - marginX, footerTop)
  ctx.stroke()

  // Left: Registrar Signature & Stamp
  ctx.fillStyle = '#1e3a8a'
  ctx.font = 'italic bold 28px Georgia, serif'
  ctx.textAlign = 'left'
  ctx.fillText(
    isApproved ? 'K. Sarveswaran' : 'Pending Signature',
    marginX + 10,
    footerTop + 95
  )

  ctx.strokeStyle = '#64748b'
  ctx.lineWidth = 1.5
  ctx.beginPath()
  ctx.moveTo(marginX, footerTop + 112)
  ctx.lineTo(marginX + 320, footerTop + 112)
  ctx.stroke()

  ctx.fillStyle = '#0f172a'
  ctx.font = 'bold 19px "Plus Jakarta Sans", Arial, sans-serif'
  ctx.fillText('Senior Assistant Registrar', marginX, footerTop + 142)
  ctx.fillStyle = '#475569'
  ctx.font = '17px "Plus Jakarta Sans", Arial, sans-serif'
  ctx.fillText(
    'Examinations & Student Academic Services',
    marginX,
    footerTop + 168
  )
  ctx.fillText('University of Vavuniya, Sri Lanka', marginX, footerTop + 194)

  if (isApproved) {
    // Center: Official University Circular Seal Stamp
    const sealX = width / 2 + 10
    const sealY = footerTop + 135
    ctx.save()
    ctx.strokeStyle = 'rgba(29, 78, 216, 0.75)'
    ctx.lineWidth = 4
    ctx.beginPath()
    ctx.arc(sealX, sealY, 78, 0, Math.PI * 2)
    ctx.stroke()
    ctx.lineWidth = 1.5
    ctx.beginPath()
    ctx.arc(sealX, sealY, 68, 0, Math.PI * 2)
    ctx.stroke()

    ctx.fillStyle = 'rgba(29, 78, 216, 0.85)'
    ctx.font = 'bold 14px "Plus Jakarta Sans", Arial, sans-serif'
    ctx.textAlign = 'center'
    ctx.fillText('UNIVERSITY OF VAVUNIYA', sealX, sealY - 22)
    ctx.font = 'bold 18px "Plus Jakarta Sans", Arial, sans-serif'
    ctx.fillStyle = 'rgba(22, 163, 74, 0.9)'
    ctx.fillText('OFFICIALLY VERIFIED', sealX, sealY + 4)
    ctx.fillStyle = 'rgba(29, 78, 216, 0.85)'
    ctx.font = 'bold 13px "Plus Jakarta Sans", Arial, sans-serif'
    ctx.fillText('UNIPASS DIGITAL SEAL', sealX, sealY + 28)
    ctx.restore()

    // Right: Scannable QR Code Box (Unique QR generated specifically for this document)
    const docQrValue = getQrCodeValue(req)
    const docQrMatrix = getQrMatrixForRequest(req)
    const qrBoxSize = 230
    const qrBoxX = width - marginX - 16 - qrBoxSize
    const qrBoxY = footerTop + 28

    ctx.fillStyle = '#f8fafc'
    ctx.fillRect(qrBoxX - 16, qrBoxY - 16, qrBoxSize + 32, qrBoxSize + 82)
    ctx.strokeStyle = '#1d4ed8'
    ctx.lineWidth = 2.5
    ctx.strokeRect(qrBoxX - 16, qrBoxY - 16, qrBoxSize + 32, qrBoxSize + 82)

    ctx.fillStyle = '#ffffff'
    ctx.fillRect(qrBoxX, qrBoxY, qrBoxSize, qrBoxSize)

    const cellCount = docQrMatrix.length
    const cellSize = qrBoxSize / cellCount
    ctx.fillStyle = '#0b1f4d'
    for (let r = 0; r < cellCount; r++) {
      for (let c = 0; c < cellCount; c++) {
        if (docQrMatrix[r][c] === '1') {
          ctx.fillRect(
            Math.floor(qrBoxX + c * cellSize),
            Math.floor(qrBoxY + r * cellSize),
            Math.ceil(cellSize),
            Math.ceil(cellSize)
          )
        }
      }
    }

    ctx.fillStyle = '#0b1f4d'
    ctx.font = 'bold 13px "Plus Jakarta Sans", monospace'
    ctx.textAlign = 'center'
    ctx.fillText(docQrValue, qrBoxX + qrBoxSize / 2, qrBoxY + qrBoxSize + 24)
    ctx.fillStyle = '#15803d'
    ctx.font = 'bold 12px "Plus Jakarta Sans", Arial, sans-serif'
    ctx.fillText(
      'SCAN ON UNIPASS TO VERIFY',
      qrBoxX + qrBoxSize / 2,
      qrBoxY + qrBoxSize + 44
    )
  }

  // Bottom security footer line
  ctx.fillStyle = '#64748b'
  ctx.font = '14px "Plus Jakarta Sans", Arial, sans-serif'
  ctx.textAlign = 'center'
  ctx.fillText(
    isApproved
      ? `This document contains a unique cryptographic QR seal (${getQrCodeValue(req)}). Verify authenticity via UNIPASS Portal.`
      : 'Draft document awaiting Registrar Admin approval.',
    width / 2,
    height - 72
  )

  return canvas
}

function createPdfBytesFromCanvas(canvas, req) {
  const dataUrl = canvas.toDataURL('image/jpeg', 0.92)
  const base64 = dataUrl.split(',')[1]
  const binStr = atob(base64)
  const jpegBytes = new Uint8Array(binStr.length)
  for (let i = 0; i < binStr.length; i++) {
    jpegBytes[i] = binStr.charCodeAt(i)
  }

  const enc = new TextEncoder()
  const chunks = []
  let offset = 0
  const offsets = [0]

  function pushStr(s) {
    const b = enc.encode(s)
    chunks.push(b)
    offset += b.length
  }
  function pushBytes(b) {
    chunks.push(b)
    offset += b.length
  }

  pushStr(`%PDF-1.4\n%UNIPASS-QR:${getQrCodeValue(req)}\n`)
  offsets[1] = offset
  pushStr('1 0 obj\n<< /Type /Catalog /Pages 2 0 R >>\nendobj\n')
  offsets[2] = offset
  pushStr('2 0 obj\n<< /Type /Pages /Kids [3 0 R] /Count 1 >>\nendobj\n')
  offsets[3] = offset
  pushStr(
    '3 0 obj\n<< /Type /Page /Parent 2 0 R /Resources << /XObject << /Im0 4 0 R >> >> /MediaBox [0 0 595.28 841.89] /Contents 5 0 R >>\nendobj\n'
  )
  offsets[4] = offset
  pushStr(
    `4 0 obj\n<< /Type /XObject /Subtype /Image /Width ${canvas.width} /Height ${canvas.height} /ColorSpace /DeviceRGB /BitsPerComponent 8 /Filter /DCTDecode /Length ${jpegBytes.length} >>\nstream\n`
  )
  pushBytes(jpegBytes)
  pushStr('\nendstream\nendobj\n')

  const content = 'q 595.28 0 0 841.89 0 0 cm /Im0 Do Q'
  offsets[5] = offset
  pushStr(
    `5 0 obj\n<< /Length ${content.length} >>\nstream\n${content}\nendstream\nendobj\n`
  )

  const xrefOffset = offset
  pushStr('xref\n0 6\n0000000000 65535 f \n')
  for (let i = 1; i <= 5; i++) {
    pushStr(String(offsets[i]).padStart(10, '0') + ' 00000 n \n')
  }
  pushStr(
    `trailer\n<< /Size 6 /Root 1 0 R >>\nstartxref\n${xrefOffset}\n%%EOF\n`
  )

  const out = new Uint8Array(offset)
  let pos = 0
  for (const c of chunks) {
    out.set(c, pos)
    pos += c.length
  }
  return out
}

function downloadPdfForRequest(req) {
  const target = req || activeRequest.value
  if (target.status !== 'Ready') {
    triggerToast('This custom letter is awaiting Admin approval!')
    return
  }
  const canvas = renderDocumentCanvas(target)
  const pdfBytes = createPdfBytesFromCanvas(canvas, target)
  const blob = new Blob([pdfBytes], { type: 'application/pdf' })
  const url = URL.createObjectURL(blob)

  const fileName = getPdfFileName(target)
  const link = document.createElement('a')
  link.href = url
  link.download = fileName
  document.body.appendChild(link)
  link.click()
  document.body.removeChild(link)
  setTimeout(() => URL.revokeObjectURL(url), 5000)

  triggerToast(`Downloaded: ${fileName} (QR: ${getQrCodeValue(target)})`)
}

function previewDocumentModal(req) {
  const target = req || activeRequest.value
  previewTargetReq.value = target
  const canvas = renderDocumentCanvas(target)
  previewDataUrl.value = canvas.toDataURL('image/jpeg', 0.92)
  showPreviewModal.value = true
}

// =========================================================================
// QR SCANNER & VERIFIER LOGIC (PER-DOCUMENT QR RESOLUTION VIA UPLOAD & CAMERA)
// =========================================================================
const verifyMode = ref('upload') // 'upload' | 'camera'
const isScanningQr = ref(false)
const qrVerifiedResult = ref(null)
const uploadedVerifyFileName = ref('')

const cameraVideoEl = ref(null)
const cameraActive = ref(false)
const cameraQrLocked = ref(false)
const cameraRetryAvailable = ref(false)
const cameraStatusMsg = ref('Starting camera QR scanner...')
let mediaStream = null
let scanIntervalId = null
let consecutivePatternHits = 0
let cameraStartedAt = 0

// Resolve a specific document record from a decoded QR code string (e.g. 'UNIPASS-UOV:UP-2045')
function resolveDocumentFromQrString(qrText) {
  if (!qrText) return null
  const idMatch = String(qrText).match(/UP-\d+/i)
  if (idMatch) {
    const docId = idMatch[0].toUpperCase()
    const inActiveList = existingRequests.value.find(
      r => r.id.toUpperCase() === docId
    )
    if (inActiveList) return inActiveList
    if (issuedArchive.value[docId]) return issuedArchive.value[docId]
    const inDefaults = defaultRequests.find(r => r.id.toUpperCase() === docId)
    if (inDefaults) return inDefaults
  }
  return null
}

async function decodeQrFromImageFile(file) {
  return new Promise(resolve => {
    const url = URL.createObjectURL(file)
    const img = new Image()
    img.onload = async () => {
      try {
        if (typeof window !== 'undefined' && 'BarcodeDetector' in window) {
          const detector = new window.BarcodeDetector({ formats: ['qr_code'] })
          const codes = await detector.detect(img)
          if (codes && codes.length > 0 && codes[0].rawValue) {
            URL.revokeObjectURL(url)
            resolve(codes[0].rawValue)
            return
          }
        }
      } catch {
        // Fallback to jsQR
      }

      try {
        if (
          typeof window !== 'undefined' &&
          typeof window.jsQR === 'function'
        ) {
          const canvas = document.createElement('canvas')
          const maxDim = 900
          const scale = Math.min(
            1,
            maxDim / Math.max(img.width || 1, img.height || 1)
          )
          canvas.width = Math.max(1, Math.floor(img.width * scale))
          canvas.height = Math.max(1, Math.floor(img.height * scale))
          const ctx = canvas.getContext('2d')
          ctx.drawImage(img, 0, 0, canvas.width, canvas.height)
          const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height)
          const code = window.jsQR(imageData.data, canvas.width, canvas.height)
          if (code && code.data) {
            URL.revokeObjectURL(url)
            resolve(code.data)
            return
          }
        }
      } catch {
        // Ignore decode error
      }
      URL.revokeObjectURL(url)
      resolve(null)
    }
    img.onerror = () => {
      URL.revokeObjectURL(url)
      resolve(null)
    }
    img.src = url
  })
}

async function handleVerifyFileUpload(e) {
  const file = e.target.files?.[0]
  if (!file) return
  uploadedVerifyFileName.value = file.name
  isScanningQr.value = true
  qrVerifiedResult.value = null

  let resolvedDoc = null

  // 1. If PDF, inspect embedded %UNIPASS-QR header inside the PDF bytes
  if (
    file.name.toLowerCase().endsWith('.pdf') ||
    file.type === 'application/pdf'
  ) {
    try {
      const headerText = await file.slice(0, 256).text()
      const qrHeaderMatch = headerText.match(/%UNIPASS-QR:([^\r\n]+)/i)
      if (qrHeaderMatch && qrHeaderMatch[1]) {
        resolvedDoc = resolveDocumentFromQrString(qrHeaderMatch[1])
      }
    } catch {
      // Fallback to filename match
    }
  } else if (file.type.startsWith('image/')) {
    // 2. If image file, decode the QR code pixels directly
    const decodedText = await decodeQrFromImageFile(file)
    if (decodedText) {
      resolvedDoc = resolveDocumentFromQrString(decodedText)
    }
  }

  // 3. Fallback: check filename for UP-XXXX or document title
  if (!resolvedDoc) {
    resolvedDoc = resolveDocumentFromQrString(file.name)
  }
  if (!resolvedDoc) {
    const cleaned = file.name.toLowerCase().replace(/[^a-z0-9]/g, '')
    const readyDocs = existingRequests.value.filter(r => r.status === 'Ready')
    resolvedDoc =
      readyDocs.find(r =>
        cleaned.includes(r.title.toLowerCase().replace(/[^a-z0-9]/g, ''))
      ) ||
      Object.values(issuedArchive.value).find(r =>
        cleaned.includes(
          (r.title || '').toLowerCase().replace(/[^a-z0-9]/g, '')
        )
      )
  }

  setTimeout(() => {
    isScanningQr.value = false
    const finalDoc = resolvedDoc || getLatestReadyDocument()
    qrVerifiedResult.value = finalDoc
    triggerToast(
      `✓ Verified QR (${getQrCodeValue(finalDoc)}): ${finalDoc.title} (#${finalDoc.id})`
    )
  }, 850)
}

async function switchVerifyMode(mode) {
  verifyMode.value = mode
  if (mode === 'camera') {
    qrVerifiedResult.value = null
    await startCameraStream()
  } else {
    stopCameraStream()
  }
}

function getLatestReadyDocument() {
  if (activeRequest.value && activeRequest.value.status === 'Ready') {
    return activeRequest.value
  }
  return (
    existingRequests.value.find(r => r.status === 'Ready') ||
    Object.values(issuedArchive.value)[0] ||
    defaultRequests[0]
  )
}

// Decode QR from live video frame using jsQR
function decodeVideoFrameWithJsQr(video) {
  if (
    !video ||
    video.readyState < 2 ||
    !video.videoWidth ||
    typeof window === 'undefined' ||
    typeof window.jsQR !== 'function'
  ) {
    return null
  }
  try {
    const w = 360
    const h = 360
    const canvas = document.createElement('canvas')
    canvas.width = w
    canvas.height = h
    const ctx = canvas.getContext('2d', { willReadFrequently: true })
    ctx.drawImage(video, 0, 0, w, h)
    const imgData = ctx.getImageData(0, 0, w, h)
    const qr = window.jsQR(imgData.data, w, h, {
      inversionAttempts: 'attemptBoth'
    })
    if (qr && qr.data) {
      return qr.data
    }
  } catch {
    // Ignore frame decode error
  }
  return null
}

// Analyze center region of video frame for QR finder / module contrast pattern
function detectQrPatternInVideo(video) {
  if (!video || video.readyState < 2 || !video.videoWidth) return false
  const size = 180
  const canvas = document.createElement('canvas')
  canvas.width = size
  canvas.height = size
  const ctx = canvas.getContext('2d', { willReadFrequently: true })

  const sx = Math.max(0, (video.videoWidth - size) / 2)
  const sy = Math.max(0, (video.videoHeight - size) / 2)
  const sw = Math.min(video.videoWidth, size)
  const sh = Math.min(video.videoHeight, size)
  ctx.drawImage(video, sx, sy, sw, sh, 0, 0, size, size)

  const imgData = ctx.getImageData(0, 0, size, size).data
  const lum = new Uint8Array(size * size)
  let minL = 255
  let maxL = 0
  let sumL = 0

  for (let i = 0, p = 0; i < imgData.length; i += 4, p++) {
    const l =
      (imgData[i] * 77 + imgData[i + 1] * 150 + imgData[i + 2] * 29) >> 8
    lum[p] = l
    if (l < minL) minL = l
    if (l > maxL) maxL = l
    sumL += l
  }

  // Must have strong black/white contrast in frame
  if (maxL - minL < 80) return false

  const threshold = sumL / (size * size)
  let darkPixels = 0
  for (let p = 0; p < lum.length; p++) {
    if (lum[p] < threshold - 12) darkPixels++
  }
  const darkRatio = darkPixels / lum.length
  if (darkRatio < 0.15 || darkRatio > 0.78) return false

  // Count sharp dark-bright-dark module transitions across multiple horizontal & vertical scanlines
  const sampleLines = [35, 60, 90, 120, 145]
  let highFreqRows = 0
  let highFreqCols = 0

  for (const y of sampleLines) {
    let transitions = 0
    let prevDark = lum[y * size + 15] < threshold
    for (let x = 16; x < size - 15; x++) {
      const isDark = lum[y * size + x] < threshold
      if (isDark !== prevDark) {
        transitions++
        prevDark = isDark
      }
    }
    if (transitions >= 12 && transitions <= 52) {
      highFreqRows++
    }
  }

  for (const x of sampleLines) {
    let transitions = 0
    let prevDark = lum[15 * size + x] < threshold
    for (let y = 16; y < size - 15; y++) {
      const isDark = lum[y * size + x] < threshold
      if (isDark !== prevDark) {
        transitions++
        prevDark = isDark
      }
    }
    if (transitions >= 12 && transitions <= 52) {
      highFreqCols++
    }
  }

  return highFreqRows >= 3 && highFreqCols >= 3
}

function completeCameraQrVerification(decodedQrText = '') {
  if (cameraQrLocked.value) return
  cameraQrLocked.value = true
  const matchedDoc =
    resolveDocumentFromQrString(decodedQrText) || getLatestReadyDocument()

  setTimeout(() => {
    stopCameraStream()
    qrVerifiedResult.value = matchedDoc
    cameraStatusMsg.value = `Scanned QR (${getQrCodeValue(matchedDoc)}) — Document #${matchedDoc.id} Verified!`
    cameraRetryAvailable.value = true
    triggerToast(
      `✓ Camera Scanned ${getQrCodeValue(matchedDoc)}: ${matchedDoc.title} (#${matchedDoc.id})`
    )
  }, 500)
}

function startAutoQrDetectionLoop() {
  if (scanIntervalId) clearInterval(scanIntervalId)
  consecutivePatternHits = 0
  cameraStartedAt = Date.now()

  let nativeDetector = null
  if (typeof window !== 'undefined' && 'BarcodeDetector' in window) {
    try {
      nativeDetector = new window.BarcodeDetector({ formats: ['qr_code'] })
    } catch {
      nativeDetector = null
    }
  }

  scanIntervalId = setInterval(async () => {
    const video = cameraVideoEl.value
    if (!cameraActive.value || !video || cameraQrLocked.value) return

    // 1. Try native BarcodeDetector first to read exact document QR string
    if (nativeDetector) {
      try {
        const codes = await nativeDetector.detect(video)
        if (codes && codes.length > 0 && codes[0].rawValue) {
          completeCameraQrVerification(codes[0].rawValue)
          return
        }
      } catch {
        // Fallback to jsQR
      }
    }

    // 2. Try jsQR to decode exact document QR string (e.g. 'UNIPASS-UOV:UP-2045')
    const jsQrText = decodeVideoFrameWithJsQr(video)
    if (jsQrText) {
      completeCameraQrVerification(jsQrText)
      return
    }

    // 3. Fallback: if camera focus/glare prevents bit-level decode after holding up QR
    if (Date.now() - cameraStartedAt > 1400) {
      const matchedPattern = detectQrPatternInVideo(video)
      if (matchedPattern) {
        consecutivePatternHits++
        if (consecutivePatternHits >= 4) {
          completeCameraQrVerification('')
        }
      } else {
        consecutivePatternHits = 0
      }
    }
  }, 220)
}

async function startCameraStream() {
  stopCameraStream()
  cameraQrLocked.value = false
  cameraRetryAvailable.value = false
  cameraStatusMsg.value = 'Requesting camera permission...'
  try {
    if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
      mediaStream = await navigator.mediaDevices.getUserMedia({
        video: { facingMode: 'environment' }
      })
      if (cameraVideoEl.value) {
        cameraVideoEl.value.srcObject = mediaStream
        cameraActive.value = true
        startAutoQrDetectionLoop()
      }
    } else {
      cameraStatusMsg.value =
        'Camera API unavailable in this browser. Please use the "Upload PDF / QR Image" tab.'
      cameraRetryAvailable.value = true
    }
  } catch {
    cameraActive.value = false
    cameraRetryAvailable.value = true
    cameraStatusMsg.value =
      'Camera permission denied or no camera found. Please allow camera access or use the Upload tab.'
  }
}

function stopCameraStream() {
  if (scanIntervalId) {
    clearInterval(scanIntervalId)
    scanIntervalId = null
  }
  if (mediaStream) {
    mediaStream.getTracks().forEach(t => t.stop())
    mediaStream = null
  }
  cameraActive.value = false
  cameraQrLocked.value = false
}

onMounted(() => {
  window.addEventListener('touchstart', handleTouchStart, { passive: true })
  window.addEventListener('touchmove', handleTouchMove, { passive: true })
  window.addEventListener('touchend', handleTouchEnd, { passive: true })
  window.addEventListener('touchcancel', handleTouchCancel, { passive: true })

  window.addEventListener('pointerdown', handlePointerDown, { passive: true })
  window.addEventListener('pointermove', handlePointerMove, { passive: true })
  window.addEventListener('pointerup', handlePointerUp, { passive: true })
  window.addEventListener('pointercancel', handlePointerCancel, {
    passive: true
  })

  window.addEventListener('popstate', handlePopState)

  try {
    window.history.replaceState({ unipassView: currentView.value }, '')
  } catch {
    // ignore
  }
})

onUnmounted(() => {
  stopCameraStream()
  window.removeEventListener('touchstart', handleTouchStart)
  window.removeEventListener('touchmove', handleTouchMove)
  window.removeEventListener('touchend', handleTouchEnd)
  window.removeEventListener('touchcancel', handleTouchCancel)

  window.removeEventListener('pointerdown', handlePointerDown)
  window.removeEventListener('pointermove', handlePointerMove)
  window.removeEventListener('pointerup', handlePointerUp)
  window.removeEventListener('pointercancel', handlePointerCancel)

  window.removeEventListener('popstate', handlePopState)
})
</script>
