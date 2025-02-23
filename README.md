<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Narratto - Open Storytelling Platform</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        /* ===== Base Styles ===== */
        :root {
            --primary: #2A2A2A;
            --accent: #E74C3C;
            --text: #333;
        }

        .exclusive-content {
            display: none; /* Hidden by default */
            position: relative;
        }

        .exclusive-content.active {
            display: block;
        }

        .members-only {
            background: rgba(0,0,0,0.8);
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: white;
        }

        /* Rest of previous CSS remains the same */
    </style>
</head>
<body>
    <!-- Header -->
    <header class="header">
        <nav class="nav">
            <h1>NARRATTO</h1>
            <div class="nav-links">
                <a href="#home">Home</a>
                <a href="#episodes">Episodes</a>
                <a href="#reality">Reality Shows</a>
                <a href="#members" id="membersLink" style="display: none;">Members</a>
            </div>
        </nav>
    </header>

    <!-- Public Content -->
    <section class="hero">
        <h2>Where Stories Come Alive</h2>
        <p>Free access to podcasts, shows, and updates</p>
    </section>

    <!-- Public Episode Library -->
    <section class="content-grid">
        <!-- Free content items -->
    </section>

    <!-- Exclusive Content Section -->
    <section class="exclusive-content" id="exclusiveSection">
        <div class="members-only" id="loginWall">
            <h3>Exclusive Content for Members</h3>
            <p>Sign up for free to access bonus material</p>
            <div class="signup-form">
                <input type="email" id="memberEmail" placeholder="Enter your email">
                <button onclick="grantAccess()">Continue</button>
            </div>
        </div>
        
        <!-- Exclusive content grid (hidden behind wall) -->
        <div class="content-grid" id="exclusiveGrid">
            <!-- Members-only content -->
        </div>
    </section>

    <script>
        function grantAccess() {
            const email = document.getElementById('memberEmail').value;
            if (email.includes('@')) {
                document.getElementById('loginWall').style.display = 'none';
                document.getElementById('exclusiveGrid').style.display = 'grid';
                document.getElementById('membersLink').style.display = 'block';
                localStorage.setItem('narrattoMember', 'true');
            }
        }

        // Check for existing access
        if(localStorage.getItem('narrattoMember')) {
            document.getElementById('exclusiveSection').classList.add('active');
            document.getElementById('membersLink').style.display = 'block';
        }
    </script>
</body>
</html>
