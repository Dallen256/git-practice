<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Youth For Christ Uganda | Enterprise Portal</title>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- EMBEDDED GLOBAL CSS STYLES -->
    <style>
        :root {
            --primary-navy: #0F2C59;
            --accent-burgundy: #800000;
            --accent-gold: #C59B27;
            --bg-gray: #F4F6F8;
            --card-white: #FFFFFF;
            --border-classic: #D1D5DB;
            --text-dark: #1F2937;
            --lock-red: #DC2626;
            --success-green: #059669;
            --sidebar-width: 240px;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: Arial, Helvetica, sans-serif;
        }

        body {
            background-color: var(--bg-gray);
            color: var(--text-dark);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        /* HEADER STYLES WITH LOGO CONTAINER */
        header {
            background-color: var(--primary-navy);
            color: white;
            padding: 0.8rem 1.5rem;
            border-bottom: 4px solid var(--accent-burgundy);
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .brand-container {
            display: flex;
            align-items: center;
            gap: 0.8rem;
        }

        .header-logo {
            width: 45px;
            height: 45px;
            background-color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: var(--primary-navy);
            border: 2px solid var(--accent-gold);
            overflow: hidden;
        }

        .header-logo img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .brand h1 {
            font-size: 1.2rem;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .brand span {
            font-size: 0.8rem;
            color: var(--accent-gold);
            display: block;
        }

        /* LAYOUT WITH SIDEBAR */
        .app-layout {
            display: flex;
            flex: 1;
        }

        /* SIDEBAR NAVIGATION */
        .sidebar {
            width: var(--sidebar-width);
            background: #1E293B;
            color: white;
            padding: 1rem 0;
            display: none; /* Shown when logged in */
            flex-direction: column;
        }

        .sidebar-menu {
            list-style: none;
        }

        .sidebar-menu li a {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            padding: 0.85rem 1.25rem;
            color: #94A3B8;
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: bold;
            transition: all 0.2s;
        }

        .sidebar-menu li a:hover, .sidebar-menu li a.active {
            background: var(--primary-navy);
            color: white;
            border-left: 4px solid var(--accent-gold);
        }

        /* MAIN CONTENT AREA */
        .main-container {
            flex: 1;
            max-width: 1200px;
            width: 100%;
            margin: 1.5rem auto;
            padding: 0 1.5rem;
        }

        .view-section {
            display: none;
        }

        .view-section.active {
            display: block;
        }

        /* BUTTONS */
        .btn-logout {
            background-color: var(--accent-burgundy);
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            font-size: 0.85rem;
            display: none;
        }

        .btn-logout:hover {
            background-color: #600000;
        }

        .btn-classic {
            background-color: var(--primary-navy);
            color: white;
            border: none;
            padding: 0.75rem 1.2rem;
            font-size: 0.9rem;
            font-weight: bold;
            border-radius: 4px;
            cursor: pointer;
            transition: background 0.2s;
            width: 100%;
        }

        .btn-classic:hover {
            background-color: var(--accent-burgundy);
        }

        .btn-small {
            padding: 0.35rem 0.65rem;
            font-size: 0.75rem;
            border-radius: 3px;
            border: none;
            cursor: pointer;
            font-weight: bold;
            color: white;
        }

        .btn-edit { background-color: var(--primary-navy); }
        .btn-delete { background-color: var(--lock-red); }
        .btn-export { background-color: var(--success-green); }

        /* CARD PANELS */
        .panel {
            background: var(--card-white);
            border: 1px solid var(--border-classic);
            border-radius: 6px;
            padding: 1.25rem;
            margin-bottom: 1.5rem;
            box-shadow: 0 2px 4px rgba(0,0,0,0.04);
        }

        .panel-header {
            font-size: 1.1rem;
            font-weight: bold;
            color: var(--accent-burgundy);
            border-bottom: 2px solid var(--primary-navy);
            padding-bottom: 0.5rem;
            margin-bottom: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 0.5rem;
        }

        /* MISSION & VISION CARDS */
        .identity-banner {
            background: linear-gradient(135deg, var(--primary-navy), #1E3A8A);
            color: white;
            border-radius: 6px;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
            gap: 1.5rem;
        }

        .portal-main-logo {
            width: 90px;
            height: 90px;
            background: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            border: 3px solid var(--accent-gold);
            flex-shrink: 0;
        }

        .portal-main-logo i {
            font-size: 2.5rem;
            color: var(--primary-navy);
        }

        .portal-main-logo img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 50%;
        }

        .mvv-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1rem;
            margin-bottom: 1.5rem;
        }

        .mvv-card {
            background: white;
            border: 1px solid var(--border-classic);
            border-top: 4px solid var(--accent-burgundy);
            padding: 1.2rem;
            border-radius: 6px;
        }

        .mvv-card.gold-top {
            border-top-color: var(--accent-gold);
        }

        .mvv-card.navy-top {
            border-top-color: var(--primary-navy);
        }

        .mvv-card h3 {
            color: var(--primary-navy);
            font-size: 1rem;
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .mvv-card p {
            font-size: 0.88rem;
            color: #4B5563;
            line-height: 1.5;
        }

        .values-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 0.75rem;
        }

        .value-item {
            background: #F8FAFC;
            border: 1px dashed var(--border-classic);
            padding: 0.75rem 1rem;
            border-radius: 4px;
            display: flex;
            align-items: center;
            gap: 0.6rem;
            font-size: 0.85rem;
            font-weight: bold;
            color: var(--primary-navy);
        }

        /* AUTHENTICATION UI CARD */
        .auth-container {
            max-width: 500px;
            margin: 2rem auto;
            background: var(--card-white);
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
            border: 1px solid var(--border-classic);
            overflow: hidden;
        }

        .auth-header-brand {
            text-align: center;
            padding: 1.5rem 1rem 0.5rem 1rem;
        }

        .auth-logo {
            width: 70px;
            height: 70px;
            margin: 0 auto 0.5rem auto;
            background: var(--bg-gray);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            border: 2px solid var(--accent-gold);
        }

        .auth-logo i {
            font-size: 2rem;
            color: var(--primary-navy);
        }

        .role-tabs {
            display: flex;
            background: #E5E7EB;
            border-bottom: 1px solid var(--border-classic);
        }

        .role-tab {
            flex: 1;
            padding: 0.8rem 0.5rem;
            text-align: center;
            font-size: 0.8rem;
            font-weight: bold;
            background: none;
            border: none;
            cursor: pointer;
            color: var(--text-dark);
            transition: all 0.2s;
        }

        .role-tab.active {
            background: var(--card-white);
            color: var(--accent-burgundy);
            border-bottom: 3px solid var(--accent-burgundy);
        }

        .auth-body {
            padding: 1.5rem;
        }

        /* FORMS & INPUTS */
        .form-group {
            margin-bottom: 1rem;
        }

        .form-group label {
            display: block;
            font-size: 0.85rem;
            font-weight: bold;
            margin-bottom: 0.3rem;
        }

        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 0.65rem;
            border: 1px solid var(--border-classic);
            border-radius: 4px;
            font-size: 0.85rem;
        }

        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 1rem;
        }

        /* STATS DASHBOARD */
        .stats-bar {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 1rem;
            margin-bottom: 1rem;
        }

        .stat-box {
            background: #F9FAFB;
            border: 1px solid var(--border-classic);
            border-left: 4px solid var(--primary-navy);
            padding: 1rem;
            text-align: center;
            border-radius: 4px;
        }

        .stat-number {
            font-size: 1.6rem;
            font-weight: bold;
            color: var(--primary-navy);
        }

        .stat-label {
            font-size: 0.75rem;
            text-transform: uppercase;
            color: #6B7280;
            font-weight: bold;
        }

        /* TABLES */
        .table-responsive {
            overflow-x: auto;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.85rem;
            margin-top: 0.5rem;
        }

        table th, table td {
            border: 1px solid var(--border-classic);
            padding: 0.65rem;
            text-align: left;
        }

        table th {
            background-color: var(--primary-navy);
            color: white;
        }

        table tr:nth-child(even) {
            background-color: #F9FAFB;
        }

        /* ALERTS AND NOTICES */
        .alert-box {
            padding: 0.75rem;
            border-radius: 4px;
            font-size: 0.85rem;
            margin-bottom: 1rem;
            display: none;
        }

        .alert-danger {
            background-color: #FEE2E2;
            color: #991B1B;
            border: 1px solid #FCA5A5;
        }

        .alert-success {
            background-color: #D1FAE5;
            color: #065F46;
            border: 1px solid #6EE7B7;
        }

        /* FEED CARDS */
        .feed-card {
            background: #FAFAFA;
            border: 1px solid var(--border-classic);
            border-left: 4px solid var(--accent-burgundy);
            padding: 0.85rem;
            margin-bottom: 0.75rem;
            border-radius: 4px;
        }

        /* MODAL STYLES */
        .modal {
            display: none;
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.5);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .modal-content {
            background: white;
            padding: 1.5rem;
            border-radius: 6px;
            width: 90%;
            max-width: 500px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        }

        footer {
            background-color: var(--primary-navy);
            color: white;
            text-align: center;
            padding: 1rem;
            font-size: 0.8rem;
            border-top: 3px solid var(--accent-gold);
            margin-top: auto;
        }

        @media (max-width: 768px) {
            .app-layout { flex-direction: column; }
            .sidebar { width: 100%; }
            .identity-banner { flex-direction: column; text-align: center; }
        }
    </style>
</head>
<body>

    <!-- BRAND HEADER WITH LOGO -->
    <header>
        <div class="brand-container">
            <div class="header-logo">
                <!-- Replace src with your official logo image link if available -->
                <i class="fa-solid fa-cross"></i>
            </div>
            <div class="brand">
                <h1>Youth For Christ Uganda</h1>
                <span id="sub-header-title">National Enterprise Portal</span>
            </div>
        </div>
        <button id="btn-logout" class="btn-logout">
            <i class="fa-solid fa-right-from-bracket"></i> Logout
        </button>
    </header>

    <div class="app-layout">
        
        <!-- SIDEBAR NAVIGATION MENU -->
        <aside id="main-sidebar" class="sidebar">
            <ul class="sidebar-menu">
                <li><a href="javascript:void(0)" class="nav-link active" data-view="home-view"><i class="fa-solid fa-house"></i> Home</a></li>
                <li><a href="javascript:void(0)" class="nav-link" data-view="dashboard-view"><i class="fa-solid fa-chart-line"></i> Analytics Dashboard</a></li>
                <li><a href="javascript:void(0)" class="nav-link" data-view="resources-view"><i class="fa-solid fa-folder-open"></i> Resources & Assets</a></li>
                <li id="nav-admin-directory" style="display:none;"><a href="javascript:void(0)" class="nav-link" data-view="admin-directory-view"><i class="fa-solid fa-users-gear"></i> Master Directory</a></li>
                <li><a href="javascript:void(0)" class="nav-link" data-view="settings-view"><i class="fa-solid fa-gear"></i> Account Settings</a></li>
            </ul>
        </aside>

        <div class="main-container">

            <!-- 1. LOGIN SECTION -->
            <section id="login-view" class="view-section active">
                <div class="auth-container">
                    <div class="auth-header-brand">
                        <div class="auth-logo">
                            <i class="fa-solid fa-cross"></i>
                        </div>
                        <h2 style="font-size: 1.1rem; color: var(--primary-navy);">Youth For Christ Uganda</h2>
                        <p style="font-size: 0.78rem; color: #666; margin-top:0.2rem;">Geared to the Times, Anchored to the Rock</p>
                    </div>

                    <div class="role-tabs">
                        <button type="button" class="role-tab active" id="tab-login-student">
                            <i class="fa-solid fa-user-graduate"></i> Student
                        </button>
                        <button type="button" class="role-tab" id="tab-login-volunteer">
                            <i class="fa-solid fa-hand-holding-heart"></i> Volunteer
                        </button>
                        <button type="button" class="role-tab" id="tab-login-host">
                            <i class="fa-solid fa-user-shield"></i> Host Admin
                        </button>
                    </div>

                    <div class="auth-body">
                        <div id="login-alert" class="alert-box"></div>

                        <form id="login-form">
                            <input type="hidden" id="login-selected-role" value="student">

                            <div class="form-group">
                                <label for="login-email">Email Address</label>
                                <input type="email" id="login-email" placeholder="user@example.com" required>
                            </div>

                            <div class="form-group">
                                <label for="login-password">Password</label>
                                <input type="password" id="login-password" placeholder="••••••••" required>
                            </div>

                            <button type="submit" class="btn-classic" id="btn-login-submit">
                                <i class="fa-solid fa-right-to-bracket"></i> Login to Portal
                            </button>
                        </form>

                        <div style="margin-top: 1rem; text-align: center; font-size: 0.85rem;">
                            <a href="javascript:void(0)" id="link-reset-password" style="color:var(--accent-burgundy); font-weight:bold;">Forgot Password?</a>
                        </div>

                        <div style="margin-top: 0.8rem; text-align: center; font-size: 0.85rem;">
                            <p>Don't have an account? <a href="javascript:void(0)" id="link-to-register" style="color:var(--primary-navy); font-weight:bold;">Register Here</a></p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- 2. REGISTER SECTION -->
            <section id="register-view" class="view-section">
                <div class="auth-container" style="max-width: 550px;">
                    <div class="auth-header-brand">
                        <div class="auth-logo">
                            <i class="fa-solid fa-cross"></i>
                        </div>
                        <h2 style="font-size: 1.1rem; color: var(--primary-navy);">Member Registration</h2>
                    </div>

                    <div class="role-tabs">
                        <button type="button" class="role-tab active" id="tab-reg-student">
                            <i class="fa-solid fa-user-graduate"></i> Student
                        </button>
                        <button type="button" class="role-tab" id="tab-reg-volunteer">
                            <i class="fa-solid fa-hand-holding-heart"></i> Volunteer
                        </button>
                    </div>

                    <div class="auth-body">
                        <div id="reg-alert" class="alert-box"></div>

                        <form id="register-form">
                            <input type="hidden" id="reg-selected-role" value="student">

                            <div class="form-group">
                                <label>Full Name</label>
                                <input type="text" id="reg-name" placeholder="John Doe" required>
                            </div>

                            <div class="form-group">
                                <label>Email Address</label>
                                <input type="email" id="reg-email" placeholder="user@example.com" required>
                            </div>

                            <div class="form-group">
                                <label>Phone Number (Private to Executive Host)</label>
                                <input type="tel" id="reg-phone" placeholder="+256 700 000 000" required>
                            </div>

                            <div class="form-group">
                                <label>Department / Ministry Scope</label>
                                <select id="reg-dept" required>
                                    <option value="Mirembe">Mirembe (Counseling & Care)</option>
                                    <option value="Ssuubi">Ssuubi (Sponsorships & Vocational)</option>
                                    <option value="Outreach">Outreach (Clubs & Evangelism)</option>
                                </select>
                            </div>

                            <div class="form-group">
                                <label>District / Residence / Institution</label>
                                <input type="text" id="reg-location" placeholder="e.g. Kampala" required>
                            </div>

                            <div class="form-group">
                                <label>Password</label>
                                <input type="password" id="reg-password" placeholder="Minimum 6 characters" minlength="6" required>
                            </div>

                            <button type="submit" class="btn-classic" id="btn-reg-submit">
                                <i class="fa-solid fa-user-plus"></i> Complete Registration
                            </button>
                        </form>

                        <div style="margin-top: 1.2rem; text-align: center; font-size: 0.85rem;">
                            <p>Already registered? <a href="javascript:void(0)" id="link-to-login" style="color:var(--primary-navy); font-weight:bold;">Login Here</a></p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- 3. HOME VIEW (VISION, MISSION & CORE VALUES INTEGRATED) -->
            <section id="home-view" class="view-section">
                <!-- HERO BRAND BANNER -->
                <div class="identity-banner">
                    <div class="portal-main-logo">
                        <i class="fa-solid fa-cross"></i>
                    </div>
                    <div>
                        <h2 style="font-size:1.5rem; font-weight:bold;">Youth For Christ Uganda</h2>
                        <p style="font-size:0.95rem; color:var(--accent-gold); font-weight:bold; margin-top:0.25rem;">
                            Geared to the Times, Anchored to the Rock
                        </p>
                        <p style="font-size:0.85rem; margin-top:0.5rem; opacity:0.9;">
                            Empowering young people, building communities, and raising lifelong followers of Jesus Christ across Uganda.
                        </p>
                    </div>
                </div>

                <!-- VISION & MISSION CARDS -->
                <div class="mvv-grid">
                    <div class="mvv-card">
                        <h3><i class="fa-solid fa-eye" style="color:var(--accent-burgundy);"></i> Our Vision</h3>
                        <p>To see every young person in Uganda given the opportunity to make an informed decision to be a follower of Jesus Christ and become a part of a local church.</p>
                    </div>

                    <div class="mvv-card gold-top">
                        <h3><i class="fa-solid fa-bullseye" style="color:var(--accent-gold);"></i> Our Mission</h3>
                        <p>To participate in the body of Christ by reaching young people in Uganda, integrating them into local churches, and discipling them into spiritual maturity.</p>
                    </div>

                    <div class="mvv-card navy-top">
                        <h3><i class="fa-solid fa-compass" style="color:var(--primary-navy);"></i> Strategic Focus</h3>
                        <p>Delivering impact through dynamic outreach programs, educational sponsorships, counseling care, and leadership development tailored to young people.</p>
                    </div>
                </div>

                <!-- CORE VALUES SECTION -->
                <div class="panel">
                    <div class="panel-header">
                        <span><i class="fa-solid fa-heart"></i> Our Core Values</span>
                    </div>
                    <div class="values-grid">
                        <div class="value-item"><i class="fa-solid fa-check-circle" style="color:var(--success-green);"></i> Evangelism & Discipleship</div>
                        <div class="value-item"><i class="fa-solid fa-check-circle" style="color:var(--success-green);"></i> Integrity & Accountability</div>
                        <div class="value-item"><i class="fa-solid fa-check-circle" style="color:var(--success-green);"></i> Servant Leadership</div>
                        <div class="value-item"><i class="fa-solid fa-check-circle" style="color:var(--success-green);"></i> Excellence in Service</div>
                        <div class="value-item"><i class="fa-solid fa-check-circle" style="color:var(--success-green);"></i> Prayer & Spiritual Passion</div>
                        <div class="value-item"><i class="fa-solid fa-check-circle" style="color:var(--success-green);"></i> Compassion & Youth Care</div>
                    </div>
                </div>

                <!-- DEPARTMENTS OVERVIEW -->
                <div class="panel">
                    <div class="panel-header">Ministry Arms & Departments</div>
                    <div class="form-grid">
                        <div class="stat-box">
                            <i class="fa-solid fa-heart-pulse" style="font-size:2rem; color:var(--accent-burgundy);"></i>
                            <h3 style="margin-top:0.5rem; font-size:1rem;">Mirembe</h3>
                            <p style="font-size:0.8rem; color:#666;">Counseling & Care Services</p>
                        </div>
                        <div class="stat-box">
                            <i class="fa-solid fa-graduation-cap" style="font-size:2rem; color:var(--primary-navy);"></i>
                            <h3 style="margin-top:0.5rem; font-size:1rem;">Ssuubi</h3>
                            <p style="font-size:0.8rem; color:#666;">Sponsorships & Skills Development</p>
                        </div>
                        <div class="stat-box">
                            <i class="fa-solid fa-bullhorn" style="font-size:2rem; color:var(--accent-gold);"></i>
                            <h3 style="margin-top:0.5rem; font-size:1rem;">Outreach</h3>
                            <p style="font-size:0.8rem; color:#666;">High School Clubs & Evangelism</p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- 4. ANALYTICS DASHBOARD VIEW -->
            <section id="dashboard-view" class="view-section">
                <div class="panel">
                    <div class="panel-header">
                        <span>Analytics Dashboard Overview</span>
                    </div>
                    <div class="stats-bar">
                        <div class="stat-box">
                            <div class="stat-number" id="stat-total">0</div>
                            <div class="stat-label">Total Registered Users</div>
                        </div>
                        <div class="stat-box">
                            <div class="stat-number" id="stat-students">0</div>
                            <div class="stat-label">Students</div>
                        </div>
                        <div class="stat-box">
                            <div class="stat-number" id="stat-volunteers">0</div>
                            <div class="stat-label">Volunteers</div>
                        </div>
                        <div class="stat-box">
                            <div class="stat-number" id="stat-uploads">0</div>
                            <div class="stat-label">Uploaded Files</div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- 5. RESOURCES & ASSETS VIEW -->
            <section id="resources-view" class="view-section">
                <div class="panel">
                    <div class="panel-header">Upload Resource / Department Asset</div>
                    <form id="upload-form">
                        <div class="form-grid">
                            <div class="form-group">
                                <label>Department:</label>
                                <select id="upload-dept" required>
                                    <option value="Mirembe">Mirembe</option>
                                    <option value="Ssuubi">Ssuubi</option>
                                    <option value="Outreach">Outreach</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label>Resource Title:</label>
                                <input type="text" id="upload-title" placeholder="e.g. Weekly Scripture Study" required>
                            </div>
                            <div class="form-group">
                                <label>File Attachment (Image, PDF, Audio, Video):</label>
                                <input type="file" id="upload-file" required>
                            </div>
                        </div>
                        <button type="submit" id="btn-upload-submit" class="btn-classic" style="margin-top: 0.5rem; width: auto;">
                            <i class="fa-solid fa-cloud-arrow-up"></i> Upload Resource
                        </button>
                    </form>
                </div>

                <div class="panel">
                    <div class="panel-header">
                        <span>Department Activity Feed</span>
                        <input type="text" id="feed-search" placeholder="Search resources..." style="padding:0.4rem; font-size:0.8rem; border:1px solid #ccc; border-radius:4px;">
                    </div>
                    <div id="resource-feed">Loading feed resources...</div>
                </div>
            </section>

            <!-- 6. MASTER DIRECTORY (HOST ADMIN ONLY) -->
            <section id="admin-directory-view" class="view-section">
                <div class="panel">
                    <div class="panel-header">
                        <span>Confidential Master Directory (Host-Only View)</span>
                        <div style="display:flex; gap:0.5rem;">
                            <input type="text" id="admin-search" placeholder="Search directory..." style="padding:0.4rem; font-size:0.8rem; border:1px solid #ccc; border-radius:4px;">
                            <button id="btn-export-csv" class="btn-small btn-export"><i class="fa-solid fa-file-csv"></i> Export CSV</button>
                        </div>
                    </div>
                    <p style="font-size:0.8rem; color:#666; margin-bottom:0.75rem;">
                        * Confidential information accessible exclusively in this Host Admin View.
                    </p>
                    <div class="table-responsive">
                        <table>
                            <thead>
                                <tr>
                                    <th>Full Name</th>
                                    <th>Role</th>
                                    <th>Department</th>
                                    <th>Phone Number</th>
                                    <th>Email Address</th>
                                    <th>Location</th>
                                    <th>Reg. Date</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody id="master-directory-tbody">
                                <tr><td colspan="8">Loading confidential directory...</td></tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- 7. ACCOUNT SETTINGS VIEW -->
            <section id="settings-view" class="view-section">
                <div class="panel">
                    <div class="panel-header">Account Settings</div>
                    <p style="font-size:0.9rem; margin-bottom:1rem;">Manage your profile and security settings.</p>
                    <button id="btn-settings-reset" class="btn-classic" style="width:auto; background-color:var(--accent-burgundy);">
                        <i class="fa-solid fa-key"></i> Request Password Reset Email
                    </button>
                </div>
            </section>

        </div>
    </div>

    <!-- EDIT USER MODAL -->
    <div id="edit-user-modal" class="modal">
        <div class="modal-content">
            <h3 style="color:var(--accent-burgundy); margin-bottom:1rem;">Edit User Details</h3>
            <form id="edit-user-form">
                <input type="hidden" id="edit-uid">
                <div class="form-group">
                    <label>Full Name</label>
                    <input type="text" id="edit-name" required>
                </div>
                <div class="form-group">
                    <label>Phone Number</label>
                    <input type="tel" id="edit-phone" required>
                </div>
                <div class="form-group">
                    <label>Department</label>
                    <select id="edit-dept" required>
                        <option value="Mirembe">Mirembe</option>
                        <option value="Ssuubi">Ssuubi</option>
                        <option value="Outreach">Outreach</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Location</label>
                    <input type="text" id="edit-location" required>
                </div>
                <div style="display:flex; gap:0.5rem; margin-top:1rem;">
                    <button type="submit" class="btn-classic">Save Changes</button>
                    <button type="button" id="btn-close-modal" class="btn-classic" style="background:#6B7280;">Cancel</button>
                </div>
            </form>
        </div>
    </div>

    <!-- FOOTER -->
    <footer>
        &copy; 2026 Youth For Christ Uganda. All Rights Reserved.
    </footer>

    <!-- ========================================== -->
    <!-- FIREBASE SYSTEM MODULE (ES MODULAR SDK)    -->
    <!-- ========================================== -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/12.1.0/firebase-app.js";
        import { getAuth, signInWithEmailAndPassword, createUserWithEmailAndPassword, signOut, onAuthStateChanged, sendPasswordResetEmail } from "https://www.gstatic.com/firebasejs/12.1.0/firebase-auth.js";
        import { getDatabase, ref as dbRef, set, get, push, onValue, update, remove } from "https://www.gstatic.com/firebasejs/12.1.0/firebase-database.js";
        import { getStorage, ref as storageRef, uploadBytes, getDownloadURL } from "https://www.gstatic.com/firebasejs/12.1.0/firebase-storage.js";

        // 1. FIREBASE CONFIG
        const firebaseConfig = {
            apiKey: "AIzaSyDApiycU8oihbWje6t6RRK_QBbiSAftfyY",
            authDomain: "yfc-portal.firebaseapp.com",
            databaseURL: "https://yfc-portal-default-rtdb.firebaseio.com",
            projectId: "yfc-portal",
            storageBucket: "yfc-portal.firebasestorage.app",
            messagingSenderId: "895126243068",
            appId: "1:895126243068:web:7529687c586669ec29f979",
            measurementId: "G-P5C5MHEPY5"
            
        };

        // Initialize Firebase
        const app = initializeApp(firebaseConfig);
        const auth = getAuth(app);
        const database = getDatabase(app);
        const storage = getStorage(app);

        let currentUser = null;
        let masterUsersList = [];

        // 2. VIEW SWITCHING & SIDEBAR LOGIC
        function switchView(viewId) {
            document.querySelectorAll('.view-section').forEach(section => section.classList.remove('active'));
            const targetSection = document.getElementById(viewId);
            if (targetSection) {
                targetSection.classList.add('active');
            }

            document.querySelectorAll('.sidebar-menu a').forEach(link => {
                if (link.getAttribute('data-view') === viewId) {
                    link.classList.add('active');
                } else {
                    link.classList.remove('active');
                }
            });

            window.scrollTo({ top: 0, behavior: 'smooth' });
        }
        window.switchView = switchView;

        // Navigation Menu Listener
        document.querySelectorAll('.sidebar-menu a').forEach(link => {
            link.addEventListener('click', (e) => {
                const targetView = e.currentTarget.getAttribute('data-view');
                if (targetView) switchView(targetView);
            });
        });

        document.addEventListener('DOMContentLoaded', () => {
            const regLink = document.getElementById('link-to-register');
            const loginLink = document.getElementById('link-to-login');

            if (regLink) regLink.addEventListener('click', () => switchView('register-view'));
            if (loginLink) loginLink.addEventListener('click', () => switchView('login-view'));
        });

        // Role tab listeners (Login)
        function selectLoginRole(role, targetBtn) {
            document.querySelectorAll('#login-view .role-tab').forEach(t => t.classList.remove('active'));
            targetBtn.classList.add('active');
            document.getElementById('login-selected-role').value = role;
        }

        document.getElementById('tab-login-student').addEventListener('click', (e) => selectLoginRole('student', e.currentTarget));
        document.getElementById('tab-login-volunteer').addEventListener('click', (e) => selectLoginRole('volunteer', e.currentTarget));
        document.getElementById('tab-login-host').addEventListener('click', (e) => selectLoginRole('host', e.currentTarget));

        // Role tab listeners (Registration)
        function selectRegRole(role, targetBtn) {
            document.querySelectorAll('#register-view .role-tab').forEach(t => t.classList.remove('active'));
            targetBtn.classList.add('active');
            document.getElementById('reg-selected-role').value = role;
        }

        document.getElementById('tab-reg-student').addEventListener('click', (e) => selectRegRole('student', e.currentTarget));
        document.getElementById('tab-reg-volunteer').addEventListener('click', (e) => selectRegRole('volunteer', e.currentTarget));

        // 3. AUTHENTICATION WATCHER
        onAuthStateChanged(auth, async (user) => {
            const logoutBtn = document.getElementById('btn-logout');
            const subTitle = document.getElementById('sub-header-title');
            const sidebar = document.getElementById('main-sidebar');
            const adminNav = document.getElementById('nav-admin-directory');

            if (user) {
                currentUser = user;
                logoutBtn.style.display = 'block';
                sidebar.style.display = 'flex';

                const userSnap = await get(dbRef(database, `users/${user.uid}`));
                if (userSnap.exists()) {
                    const userData = userSnap.val();
                    
                    if (userData.role === 'host' || userData.role === 'admin') {
                        subTitle.innerText = `Host Admin: ${userData.name}`;
                        adminNav.style.display = 'block';
                        switchView('dashboard-view');
                        loadAdminData();
                    } else {
                        subTitle.innerText = `${userData.role.toUpperCase()}: ${userData.name}`;
                        adminNav.style.display = 'none';
                        switchView('home-view');
                        listenToFeed();
                    }
                }
            } else {
                currentUser = null;
                logoutBtn.style.display = 'none';
                sidebar.style.display = 'none';
                subTitle.innerText = "National Enterprise Portal";
                switchView('login-view');
            }
        });

        // 4. LOGIN FORM
        document.getElementById('login-form').addEventListener('submit', async (e) => {
            e.preventDefault();
            const alertBox = document.getElementById('login-alert');
            alertBox.style.display = 'none';

            const email = document.getElementById('login-email').value.trim();
            const password = document.getElementById('login-password').value;
            const selectedRole = document.getElementById('login-selected-role').value;
            const btn = document.getElementById('btn-login-submit');

            btn.disabled = true;
            btn.innerHTML = '<i class="fa-solid fa-spinner fa-spin"></i> Authenticating...';

            try {
                const userCredential = await signInWithEmailAndPassword(auth, email, password);
                const user = userCredential.user;

                const userSnap = await get(dbRef(database, `users/${user.uid}`));
                if (userSnap.exists()) {
                    const userData = userSnap.val();
                    if (selectedRole === 'host' && (userData.role !== 'host' && userData.role !== 'admin')) {
                        alertBox.textContent = "Access Denied: You do not have Host Executive clearance.";
                        alertBox.className = "alert-box alert-danger";
                        alertBox.style.display = "block";
                        btn.disabled = false;
                        btn.innerHTML = '<i class="fa-solid fa-right-to-bracket"></i> Login to Portal';
                        return;
                    }
                }
            } catch (err) {
                alertBox.textContent = err.message || "Invalid credentials.";
                alertBox.className = "alert-box alert-danger";
                alertBox.style.display = "block";
                btn.disabled = false;
                btn.innerHTML = '<i class="fa-solid fa-right-to-bracket"></i> Login to Portal';
            }
        });

        // PASSWORD RESET HANDLERS
        const triggerPasswordReset = async () => {
            const email = currentUser ? currentUser.email : prompt("Enter your email address to receive a password reset link:");
            if (email) {
                try {
                    await sendPasswordResetEmail(auth, email.trim());
                    alert("Password reset email sent! Please check your inbox.");
                } catch (err) {
                    alert("Failed to send reset email: " + err.message);
                }
            }
        };

        document.getElementById('link-reset-password').addEventListener('click', triggerPasswordReset);
        document.getElementById('btn-settings-reset').addEventListener('click', triggerPasswordReset);

        // 5. REGISTRATION FORM
        document.getElementById('register-form').addEventListener('submit', async (e) => {
            e.preventDefault();
            const alertBox = document.getElementById('reg-alert');
            alertBox.style.display = 'none';

            const name = document.getElementById('reg-name').value.trim();
            const email = document.getElementById('reg-email').value.trim();
            const phone = document.getElementById('reg-phone').value.trim();
            const dept = document.getElementById('reg-dept').value;
            const location = document.getElementById('reg-location').value.trim();
            const password = document.getElementById('reg-password').value;
            const role = document.getElementById('reg-selected-role').value;
            const btn = document.getElementById('btn-reg-submit');

            btn.disabled = true;
            btn.innerHTML = '<i class="fa-solid fa-spinner fa-spin"></i> Registering...';

            try {
                const cred = await createUserWithEmailAndPassword(auth, email, password);
                
                await set(dbRef(database, `users/${cred.user.uid}`), {
                    uid: cred.user.uid,
                    name: name,
                    email: email,
                    phone: phone,
                    dept: dept,
                    location: location,
                    role: role,
                    createdAt: new Date().toISOString()
                });

                alertBox.textContent = "Registration Successful! Redirecting...";
                alertBox.className = "alert-box alert-success";
                alertBox.style.display = "block";

            } catch (err) {
                alertBox.textContent = err.message;
                alertBox.className = "alert-box alert-danger";
                alertBox.style.display = "block";
                btn.disabled = false;
                btn.innerHTML = '<i class="fa-solid fa-user-plus"></i> Complete Registration';
            }
        });

        // 6. LOGOUT
        document.getElementById('btn-logout').addEventListener('click', () => {
            signOut(auth);
        });

        // 7. FILE UPLOAD
        document.getElementById('upload-form').addEventListener('submit', async (e) => {
            e.preventDefault();
            const dept = document.getElementById('upload-dept').value;
            const title = document.getElementById('upload-title').value.trim();
            const file = document.getElementById('upload-file').files[0];
            const btn = document.getElementById('btn-upload-submit');

            if (!file) return alert("Please select a file first.");

            btn.disabled = true;
            btn.innerHTML = '<i class="fa-solid fa-spinner fa-spin"></i> Uploading...';

            try {
                const sRef = storageRef(storage, `uploads/${Date.now()}_${file.name}`);
                await uploadBytes(sRef, file);
                const downloadUrl = await getDownloadURL(sRef);

                await push(dbRef(database, 'uploads'), {
                    dept: dept,
                    title: title,
                    fileUrl: downloadUrl,
                    fileName: file.name,
                    uploadedBy: currentUser ? currentUser.uid : 'Anonymous',
                    timestamp: new Date().toISOString()
                });

                alert("Resource uploaded successfully!");
                document.getElementById('upload-form').reset();
            } catch (err) {
                alert("Upload failed: " + err.message);
            } finally {
                btn.disabled = false;
                btn.innerHTML = '<i class="fa-solid fa-cloud-arrow-up"></i> Upload Resource';
            }
        });

        // 8. REALTIME FEED
        function listenToFeed() {
            onValue(dbRef(database, 'uploads'), (snap) => {
                const feedContainer = document.getElementById('resource-feed');
                if (!snap.exists()) {
                    feedContainer.innerHTML = '<p style="font-size:0.85rem; color:#666;">No resources uploaded yet.</p>';
                    return;
                }

                const items = Object.values(snap.val()).reverse();
                feedContainer.innerHTML = items.map(item => `
                    <div class="feed-card">
                        <div style="font-weight:bold; color:var(--primary-navy);">[${item.dept}] ${item.title}</div>
                        <div style="font-size:0.8rem; color:#555; margin-top:0.25rem;">Uploaded: ${new Date(item.timestamp).toLocaleString()}</div>
                        <a href="${item.fileUrl}" target="_blank" style="display:inline-block; margin-top:0.5rem; color:var(--accent-burgundy); font-weight:bold; font-size:0.85rem;">
                            <i class="fa-solid fa-paperclip"></i> Access Attachment (${item.fileName})
                        </a>
                    </div>
                `).join('');
            });
        }

        // 9. HOST ADMIN DATA & ACTIONS
        async function loadAdminData() {
            const tbody = document.getElementById('master-directory-tbody');
            const usersSnap = await get(dbRef(database, 'users'));
            const uploadsSnap = await get(dbRef(database, 'uploads'));

            if (!usersSnap.exists()) {
                tbody.innerHTML = '<tr><td colspan="8">No registered user records found.</td></tr>';
                return;
            }

            masterUsersList = Object.values(usersSnap.val());
            const uploadsCount = uploadsSnap.exists() ? Object.keys(uploadsSnap.val()).length : 0;

            const studentsCount = masterUsersList.filter(u => u.role === 'student').length;
            const volunteersCount = masterUsersList.filter(u => u.role === 'volunteer').length;

            document.getElementById('stat-total').innerText = masterUsersList.length;
            document.getElementById('stat-students').innerText = studentsCount;
            document.getElementById('stat-volunteers').innerText = volunteersCount;
            document.getElementById('stat-uploads').innerText = uploadsCount;

            renderAdminTable(masterUsersList);
        }

        function renderAdminTable(data) {
            const tbody = document.getElementById('master-directory-tbody');
            tbody.innerHTML = data.map(u => `
                <tr>
                    <td><strong>${u.name || 'N/A'}</strong></td>
                    <td><span style="background:${u.role==='volunteer'?'#2563EB':'#059669'}; color:white; padding:2px 6px; border-radius:3px; font-size:0.7rem; font-weight:bold;">${u.role || 'Member'}</span></td>
                    <td>${u.dept || 'N/A'}</td>
                    <td><strong style="color:var(--primary-navy);">${u.phone || 'N/A'}</strong></td>
                    <td>${u.email || 'N/A'}</td>
                    <td>${u.location || 'N/A'}</td>
                    <td>${u.createdAt ? new Date(u.createdAt).toLocaleDateString() : 'N/A'}</td>
                    <td>
                        <button class="btn-small btn-edit" onclick="openEditModal('${u.uid}')"><i class="fa-solid fa-pen"></i></button>
                        <button class="btn-small btn-delete" onclick="deleteUserRecord('${u.uid}')"><i class="fa-solid fa-trash"></i></button>
                    </td>
                </tr>
            `).join('');
        }

        // EDIT & DELETE HANDLERS
        window.openEditModal = (uid) => {
            const user = masterUsersList.find(u => u.uid === uid);
            if (!user) return;

            document.getElementById('edit-uid').value = user.uid;
            document.getElementById('edit-name').value = user.name || '';
            document.getElementById('edit-phone').value = user.phone || '';
            document.getElementById('edit-dept').value = user.dept || 'Mirembe';
            document.getElementById('edit-location').value = user.location || '';
            
            document.getElementById('edit-user-modal').style.display = 'flex';
        };

        document.getElementById('btn-close-modal').addEventListener('click', () => {
            document.getElementById('edit-user-modal').style.display = 'none';
        });

        document.getElementById('edit-user-form').addEventListener('submit', async (e) => {
            e.preventDefault();
            const uid = document.getElementById('edit-uid').value;
            
            try {
                await update(dbRef(database, `users/${uid}`), {
                    name: document.getElementById('edit-name').value.trim(),
                    phone: document.getElementById('edit-phone').value.trim(),
                    dept: document.getElementById('edit-dept').value,
                    location: document.getElementById('edit-location').value.trim()
                });
                alert("User record updated successfully!");
                document.getElementById('edit-user-modal').style.display = 'none';
                loadAdminData();
            } catch (err) {
                alert("Update failed: " + err.message);
            }
        });

        window.deleteUserRecord = async (uid) => {
            if (confirm("Are you sure you want to delete this user record from the Realtime Database?")) {
                try {
                    await remove(dbRef(database, `users/${uid}`));
                    alert("User record removed!");
                    loadAdminData();
                } catch (err) {
                    alert("Delete failed: " + err.message);
                }
            }
        };

        // EXPORT TO CSV REPORT
        document.getElementById('btn-export-csv').addEventListener('click', () => {
            if (!masterUsersList.length) return alert("No data available to export.");

            const headers = ["UID", "Name", "Role", "Department", "Phone", "Email", "Location", "Registration Date"];
            const rows = masterUsersList.map(u => [
                u.uid || '',
                `"${u.name || ''}"`,
                u.role || '',
                u.dept || '',
                `"${u.phone || ''}"`,
                u.email || '',
                `"${u.location || ''}"`,
                u.createdAt || ''
            ]);

            const csvContent = "data:text/csv;charset=utf-8," + [headers.join(','), ...rows.map(e => e.join(','))].join('\n');
            const encodedUri = encodeURI(csvContent);
            const link = document.createElement("a");
            link.setAttribute("href", encodedUri);
            link.setAttribute("download", `YFC_Master_Directory_${new Date().toISOString().slice(0,10)}.csv`);
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        });

        // 10. SEARCH FILTERS
        document.getElementById('feed-search').addEventListener('keyup', () => {
            const query = document.getElementById('feed-search').value.toLowerCase();
            const cards = document.querySelectorAll('#resource-feed .feed-card');
            cards.forEach(card => {
                card.style.display = card.textContent.toLowerCase().includes(query) ? 'block' : 'none';
            });
        });

        document.getElementById('admin-search').addEventListener('keyup', () => {
            const query = document.getElementById('admin-search').value.toLowerCase();
            const filtered = masterUsersList.filter(u => 
                (u.name && u.name.toLowerCase().includes(query)) ||
                (u.phone && u.phone.toLowerCase().includes(query)) ||
                (u.email && u.email.toLowerCase().includes(query)) ||
                (u.location && u.location.toLowerCase().includes(query))
            );
            renderAdminTable(filtered);
        });
    </script>
</body>
</html>
