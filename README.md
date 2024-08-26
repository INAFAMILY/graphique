<!DOCTYPE html>
<html>
  <head>
    <title>Exemple de Google Charts</title>
    <!-- Charger la bibliothèque de Google Charts -->
    <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
    <script type="text/javascript">
      // Charger la version actuelle de Google Charts avec les packages nécessaires
      google.charts.load('current', {'packages':['corechart', 'bar', 'table', 'gauge', 'geochart', 'treemap', 'orgchart']});

      // Définir une fonction pour dessiner tous les graphiques
      google.charts.setOnLoadCallback(drawCharts);

      function drawCharts() {
        // 1. Graphique Linéaire
        var dataLine = google.visualization.arrayToDataTable([
          ['Année', 'Ventes'],
          ['2018',  1000],
          ['2019',  1170],
          ['2020',  660],
          ['2021',  1030]
        ]);

        var optionsLine = {
          title: 'Ventes annuelles',
          curveType: 'function',
          legend: { position: 'bottom' }
        };

        var chartLine = new google.visualization.LineChart(document.getElementById('linechart_div'));
        chartLine.draw(dataLine, optionsLine);

        // 2. Graphique Circulaire
        var dataPie = google.visualization.arrayToDataTable([
          ['Tâche', 'Heures par jour'],
          ['Travail', 8],
          ['Manger', 2],
          ['Commute', 2],
          ['Regarder la TV', 2],
          ['Dormir', 8]
        ]);

        var optionsPie = {
          title: 'Mes activités quotidiennes'
        };

        var chartPie = new google.visualization.PieChart(document.getElementById('piechart_div'));
        chartPie.draw(dataPie, optionsPie);

        // 3. Nuage de Points
        var dataScatter = google.visualization.arrayToDataTable([
          ['Âge', 'Taille'],
          [ 8,      4 ],
          [ 4,      5.5 ],
          [ 11,     6 ],
          [ 4,      4 ],
          [ 3,      3.5 ],
          [ 6.5,    7 ]
        ]);

        var optionsScatter = {
          title: 'Corrélation entre âge et taille',
          hAxis: {title: 'Âge'},
          vAxis: {title: 'Taille'},
          legend: 'none'
        };

        var chartScatter = new google.visualization.ScatterChart(document.getElementById('scatterchart_div'));
        chartScatter.draw(dataScatter, optionsScatter);

        // 4. Histogramme
        var dataHistogram = google.visualization.arrayToDataTable([
          ['Dinosaur', 'Length'],
          ['Acrocanthosaurus (top-spined lizard)', 12.2],
          ['Albertosaurus (Alberta lizard)', 9.1],
          ['Allosaurus (other lizard)', 12.2],
          ['Apatosaurus (deceptive lizard)', 22.9],
          ['Archaeopteryx (ancient wing)', 0.9],
          ['Argentinosaurus (Argentina lizard)', 36.6],
          ['Baryonyx (heavy claws)', 9.1],
          ['Brachiosaurus (arm lizard)', 30.5],
          ['Ceratosaurus (horned lizard)', 6.1],
          ['Coelophysis (hollow form)', 2.7],
          ['Compsognathus (elegant jaw)', 0.9],
          ['Deinonychus (terrible claw)', 2.7],
          ['Diplodocus (double beam)', 27.1],
          ['Dromicelomimus (emu mimic)', 3.4],
          ['Gallimimus (fowl mimic)', 5.5],
          ['Mamenchisaurus (Mamenchi lizard)', 21.0],
          ['Megalosaurus (big lizard)', 7.9],
          ['Microvenator (small hunter)', 1.2],
          ['Ornithomimus (bird mimic)', 4.6],
          ['Oviraptor (egg robber)', 1.5],
          ['Plateosaurus (flat lizard)', 7.9],
          ['Sauronithoides (Sauron's lizard)', 2.0],
          ['Seismosaurus (tremor lizard)', 45.7],
          ['Spinosaurus (spiny lizard)', 12.2],
          ['Supersaurus (super lizard)', 30.5],
          ['Tyrannosaurus (tyrant lizard)', 15.2],
          ['Ultrasaurus (ultra lizard)', 30.5],
          ['Velociraptor (swift seizer)', 1.8]
        ]);

        var optionsHistogram = {
          title: 'Longueur des Dinosaures',
          legend: { position: 'none' },
        };

        var chartHistogram = new google.visualization.Histogram(document.getElementById('histogram_div'));
        chartHistogram.draw(dataHistogram, optionsHistogram);

        // 5. Graphique Géographique
        var dataGeo = google.visualization.arrayToDataTable([
          ['Country', 'Popularity'],
          ['Germany', 200],
          ['United States', 300],
          ['Brazil', 400],
          ['Canada', 500],
          ['France', 600],
          ['RU', 700]
        ]);

        var optionsGeo = {
          region: 'world',
          displayMode: 'regions',
          colorAxis: {colors: ['#e7711c', '#4374e0']}
        };

        var chartGeo = new google.visualization.GeoChart(document.getElementById('geochart_div'));
        chartGeo.draw(dataGeo, optionsGeo);

        // 6. Graphique à Colonnes
        var dataColumn = google.visualization.arrayToDataTable([
          ['City', '2010 Population', '2000 Population'],
          ['New York City, NY', 8175000, 8008000],
          ['Los Angeles, CA', 3792000, 3694000],
          ['Chicago, IL', 2695000, 2896000],
          ['Houston, TX', 2099000, 1953000],
          ['Philadelphia, PA', 1526000, 1517000]
        ]);

        var optionsColumn = {
          chart: {
            title: 'Population des plus grandes villes',
            subtitle: 'Comparaison de la population en 2000 et 2010'
          }
        };

        var chartColumn = new google.visualization.ColumnChart(document.getElementById('columnchart_div'));
        chartColumn.draw(dataColumn, optionsColumn);

        // 7. Graphique à Barres
        var dataBar = google.visualization.arrayToDataTable([
          ['Year', 'Sales', 'Expenses'],
          ['2014', 1000, 400],
          ['2015', 1170, 460],
          ['2016', 660, 1120],
          ['2017', 1030, 540]
        ]);

        var optionsBar = {
          chart: {
            title: 'Performance des ventes',
            subtitle: 'Ventes et dépenses : 2014-2017',
          }
        };

        var chartBar = new google.visualization.BarChart(document.getElementById('barchart_div'));
        chartBar.draw(dataBar, optionsBar);

        // 8. Graphique Combiné
        var dataCombo = google.visualization.arrayToDataTable([
          ['Month', 'Bolivia', 'Ecuador', 'Madagascar', 'Papua New Guinea', 'Rwanda', 'Average'],
          ['2004/05',  165,      938,         522,             998,           450,      614.6],
          ['2005/06',  135,      1120,        599,             1268,          288,      682],
          ['2006/07',  157,      1167,        587,             807,           397,      623],
          ['2007/08',  139,      1110,        615,             968,           215,      609.4],
          ['2008/09',  136,      691,         629,             1026,          366,      569]
        ]);

        var optionsCombo = {
         
