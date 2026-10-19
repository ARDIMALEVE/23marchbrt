<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Live Leaderboard - Backyard Ultra</title>
    <!-- Tailwind CSS përmes CDN për stilim të shpejtë dhe falas -->
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-zinc-950 text-zinc-100 font-sans min-h-screen p-4 md:p-8">

    <div class="max-w-5xl mx-auto">
        <!-- Header -->
        <header class="flex flex-col md:flex-row justify-between items-center border-b border-zinc-800 pb-6 mb-6">
            <h1 class="text-2xl font-black tracking-wider text-amber-500">SURVIVE THE BACKYARD</h1>
            <div class="mt-2 md:mt-0 bg-zinc-900 border border-zinc-800 px-4 py-1.5 rounded-full text-sm font-semibold text-emerald-400">
                STATUS: FINISHED
            </div>
        </header>

        <!-- Fituesi / Informacioni Kryesor -->
        <div class="bg-zinc-900 border border-zinc-800 rounded-xl p-6 mb-8 text-center shadow-lg">
            <p class="text-zinc-400 text-sm uppercase tracking-widest mb-1">Fituesi i Garës</p>
            <h2 class="text-3xl font-bold text-white">🏆 Ali Kansu (#9) - <span class="text-amber-500">24 Yards</span></h2>
        </div>

        <!-- Fusha e Kërkimit -->
        <div class="mb-6">
            <input type="text" id="searchInput" placeholder="Kërko vrapues ose numrin (bib)..." 
                class="w-full bg-zinc-900 border border-zinc-800 rounded-lg px-4 py-3 text-zinc-100 focus:outline-none focus:border-amber-500 transition-colors"
                onkeyup="searchTable()">
        </div>

        <!-- Tabela e Rezultateve -->
        <div class="overflow-x-auto border border-zinc-800 rounded-xl bg-zinc-900">
            <table id="leaderboardTable" class="w-full text-left border-collapse">
                <thead>
                    <tr class="border-b border-zinc-800 text-zinc-400 text-xs uppercase bg-zinc-900/50">
                        <th class="p-4">Rank</th>
                        <th class="p-4">Vrapuesi</th>
                        <th class="p-4">Yards</th>
                        <th class="p-4">Distanca</th>
                        <th class="p-4">Statusi</th>
                    </tr>
                </thead>
                <tbody class="divide-y divide-zinc-800 text-sm">
                    <tr class="hover:bg-zinc-800/50 transition-colors">
                        <td class="p-4 font-bold text-amber-500">01</td>
                        <td class="p-4 font-medium">9 - Ali Kansu <span class="text-xs text-zinc-500 block">Turkey · Ultra</span></td>
                        <td class="p-4 font-bold">23</td>
                        <td class="p-4 text-zinc-400">154.2 km</td>
                        <td class="p-4"><span class="bg-amber-500/10 text-amber-500 border border-amber-500/20 px-2.5 py-1 rounded text-xs font-bold">WINNER</span></td>
                    </tr>
                    <tr class="hover:bg-zinc-800/50 transition-colors">
                        <td class="p-4 font-bold text-zinc-400">02</td>
                        <td class="p-4 font-medium">26 - Fatmir Tahiri <span class="text-xs text-zinc-500 block">Kosovo · Ultra</span></td>
                        <td class="p-4 font-bold">22</td>
                        <td class="p-4 text-zinc-400">147.5 km</td>
                        <td class="p-4"><span class="bg-zinc-800 text-zinc-400 px-2.5 py-1 rounded text-xs">DNF</span></td>
                    </tr>
                    <tr class="hover:bg-zinc-800/50 transition-colors">
                        <td class="p-4 font-bold text-zinc-400">18</td>
                        <td class="p-4 font-medium">12 - Ardian Sadiku <span class="text-xs text-zinc-500 block">Kosovo · Ultra · NEW PB</span></td>
                        <td class="p-4 font-bold">11</td>
                        <td class="p-4 text-zinc-400">73.8 km</td>
                        <td class="p-4"><span class="bg-zinc-800 text-zinc-400 px-2.5 py-1 rounded text-xs">DNF</span></td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>

    <!-- Skripta e Kërkimit në Kohë Reale -->
    <script>
        function searchTable() {
            let input = document.getElementById("searchInput");
            let filter = input.value.toLowerCase();
            let table = document.getElementById("leaderboardTable");
            let tr = table.getElementsByTagName("tr");

            for (let i = 1; i < tr.length; i++) {
                let td = tr[i].getElementsByTagName("td")[1];
                if (td) {
                    let txtValue = td.textContent || td.innerText;
                    if (txtValue.toLowerCase().indexOf(filter) > -1) {
                        tr[i].style.display = "";
                    } else {
                        tr[i].style.display = "none";
                    }
                }
            }
        }
    </script>
</body>
</html>
