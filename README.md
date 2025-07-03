<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Análisis de Mínimos Cuadrados</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.9.1/chart.min.js"></script>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            backdrop-filter: blur(10px);
        }
        
        h1 {
            text-align: center;
            color: #2c3e50;
            margin-bottom: 30px;
            font-size: 2.5em;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .section {
            margin-bottom: 40px;
            padding: 25px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            border-left: 5px solid #3498db;
        }
        
        .section h2 {
            color: #2980b9;
            margin-bottom: 20px;
            font-size: 1.8em;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            font-size: 16px;
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        th, td {
            padding: 15px;
            text-align: center;
            border-bottom: 1px solid #ddd;
        }
        
        th {
            background: linear-gradient(135deg, #3498db, #2980b9);
            color: white;
            font-weight: 600;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
        }
        
        tr:hover {
            background-color: #f8f9fa;
            transform: scale(1.01);
            transition: all 0.3s ease;
        }
        
        .chart-container {
            position: relative;
            height: 500px;
            margin: 30px 0;
            background: white;
            border-radius: 15px;
            padding: 20px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
        }
        
        .result-highlight {
            background: linear-gradient(135deg, #2ecc71, #27ae60);
            color: white;
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            font-size: 1.3em;
            font-weight: bold;
            margin: 20px 0;
            box-shadow: 0 8px 25px rgba(46, 204, 113, 0.3);
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { box-shadow: 0 8px 25px rgba(46, 204, 113, 0.3); }
            50% { box-shadow: 0 8px 35px rgba(46, 204, 113, 0.5); }
            100% { box-shadow: 0 8px 25px rgba(46, 204, 113, 0.3); }
        }
        
        .equation {
            font-size: 1.2em;
            font-weight: bold;
            color: #2c3e50;
            text-align: center;
            margin: 10px 0;
            padding: 15px;
            background: #ecf0f1;
            border-radius: 10px;
            border: 2px solid #bdc3c7;
        }
        
        .error-cell {
            font-weight: bold;
        }
        
        .option-a { background-color: #e8f5e8 !important; }
        .option-b { background-color: #fff5e6 !important; }
        .option-c { background-color: #f0f8ff !important; }
        
        .summary-table {
            max-width: 500px;
            margin: 20px auto;
        }
        
        .summary-table th {
            background: linear-gradient(135deg, #e74c3c, #c0392b);
        }
        
        .winner {
            background: linear-gradient(135deg, #2ecc71, #27ae60) !important;
            color: white !important;
            font-weight: bold;
        }
        
        .fraction {
            font-size: 1.1em;
        }
        
        .calculation-details {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 10px;
            margin: 10px 0;
            border-left: 4px solid #3498db;
        }
        
        .step-by-step {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            gap: 15px;
            margin: 20px 0;
        }
        
        .step-card {
            background: white;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>📊 Análisis de Mínimos Cuadrados</h1>
        
        <div class="section">
            <h2>📋 Datos Originales</h2>
            <table>
                <thead>
                    <tr>
                        <th>Punto</th>
                        <th>x</th>
                        <th>y</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>1</td>
                        <td>1</td>
                        <td>2</td>
                    </tr>
                    <tr>
                        <td>2</td>
                        <td>2</td>
                        <td>2</td>
                    </tr>
                    <tr>
                        <td>3</td>
                        <td>3</td>
                        <td>4</td>
                    </tr>
                </tbody>
            </table>
        </div>

        <div class="section">
            <h2>📈 Opción a) y = 1 + x</h2>
            <div class="equation">y = 1 + x</div>
            <table>
                <thead>
                    <tr>
                        <th>x</th>
                        <th>y observado</th>
                        <th>y predicho</th>
                        <th>Error (e)</th>
                        <th>Error² (e²)</th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="option-a">
                        <td>1</td>
                        <td>2</td>
                        <td>1 + 1 = 2</td>
                        <td>2 - 2 = 0</td>
                        <td>0² = 0</td>
                    </tr>
                    <tr class="option-a">
                        <td>2</td>
                        <td>2</td>
                        <td>1 + 2 = 3</td>
                        <td>2 - 3 = -1</td>
                        <td>(-1)² = 1</td>
                    </tr>
                    <tr class="option-a">
                        <td>3</td>
                        <td>4</td>
                        <td>1 + 3 = 4</td>
                        <td>4 - 4 = 0</td>
                        <td>0² = 0</td>
                    </tr>
                    <tr class="option-a">
                        <td colspan="4"><strong>Suma de Errores Cuadráticos (SSE)</strong></td>
                        <td class="error-cell"><strong>1</strong></td>
                    </tr>
                </tbody>
            </table>
        </div>

        <div class="section">
            <h2>📈 Opción b) y = -2 + 2x</h2>
            <div class="equation">y = -2 + 2x</div>
            <table>
                <thead>
                    <tr>
                        <th>x</th>
                        <th>y observado</th>
                        <th>y predicho</th>
                        <th>Error (e)</th>
                        <th>Error² (e²)</th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="option-b">
                        <td>1</td>
                        <td>2</td>
                        <td>-2 + 2(1) = 0</td>
                        <td>2 - 0 = 2</td>
                        <td>2² = 4</td>
                    </tr>
                    <tr class="option-b">
                        <td>2</td>
                        <td>2</td>
                        <td>-2 + 2(2) = 2</td>
                        <td>2 - 2 = 0</td>
                        <td>0² = 0</td>
                    </tr>
                    <tr class="option-b">
                        <td>3</td>
                        <td>4</td>
                        <td>-2 + 2(3) = 4</td>
                        <td>4 - 4 = 0</td>
                        <td>0² = 0</td>
                    </tr>
                    <tr class="option-b">
                        <td colspan="4"><strong>Suma de Errores Cuadráticos (SSE)</strong></td>
                        <td class="error-cell"><strong>4</strong></td>
                    </tr>
                </tbody>
            </table>
        </div>

        <div class="section">
            <h2>📈 Opción c) y = 2/3 + x</h2>
            <div class="equation">y = <span class="fraction">2/3</span> + x ≈ 0.667 + x</div>
            
            <div class="calculation-details">
                <h4>🧮 Cálculos Detallados:</h4>
                <div class="step-by-step">
                    <div class="step-card">
                        <strong>Punto (1, 2)</strong><br>
                        y_pred = 2/3 + 1 = 5/3 ≈ 1.667<br>
                        Error = 2 - 5/3 = 1/3 ≈ 0.333<br>
                        Error² = (1/3)² = 1/9 ≈ 0.111
                    </div>
                    <div class="step-card">
                        <strong>Punto (2, 2)</strong><br>
                        y_pred = 2/3 + 2 = 8/3 ≈ 2.667<br>
                        Error = 2 - 8/3 = -2/3 ≈ -0.667<br>
                        Error² = (-2/3)² = 4/9 ≈ 0.444
                    </div>
                    <div class="step-card">
                        <strong>Punto (3, 4)</strong><br>
                        y_pred = 2/3 + 3 = 11/3 ≈ 3.667<br>
                        Error = 4 - 11/3 = 1/3 ≈ 0.333<br>
                        Error² = (1/3)² = 1/9 ≈ 0.111
                    </div>
                </div>
            </div>
            
            <table>
                <thead>
                    <tr>
                        <th>x</th>
                        <th>y observado</th>
                        <th>y predicho</th>
                        <th>Error (e)</th>
                        <th>Error² (e²)</th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="option-c">
                        <td>1</td>
                        <td>2</td>
                        <td>2/3 + 1 = 5/3 ≈ 1.667</td>
                        <td>2 - 5/3 = 1/3 ≈ 0.333</td>
                        <td>(1/3)² = 1/9 ≈ 0.111</td>
                    </tr>
                    <tr class="option-c">
                        <td>2</td>
                        <td>2</td>
                        <td>2/3 + 2 = 8/3 ≈ 2.667</td>
                        <td>2 - 8/3 = -2/3 ≈ -0.667</td>
                        <td>(-2/3)² = 4/9 ≈ 0.444</td>
                    </tr>
                    <tr class="option-c">
                        <td>3</td>
                        <td>4</td>
                        <td>2/3 + 3 = 11/3 ≈ 3.667</td>
                        <td>4 - 11/3 = 1/3 ≈ 0.333</td>
                        <td>(1/3)² = 1/9 ≈ 0.111</td>
                    </tr>
                    <tr class="option-c winner">
                        <td colspan="4"><strong>Suma de Errores Cuadráticos (SSE)</strong></td>
                        <td class="error-cell"><strong>1/9 + 4/9 + 1/9 = 6/9 = 2/3 ≈ 0.667</strong></td>
                    </tr>
                </tbody>
            </table>
        </div>

        <div class="section">
            <h2>📊 Resumen de Resultados</h2>
            <table class="summary-table">
                <thead>
                    <tr>
                        <th>Opción</th>
                        <th>Ecuación</th>
                        <th>SSE (Fracción)</th>
                        <th>SSE (Decimal)</th>
                        <th>Ranking</th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="winner">
                        <td>c)</td>
                        <td>y = 2/3 + x</td>
                        <td>2/3</td>
                        <td>0.667</td>
                        <td>🏆 1º</td>
                    </tr>
                    <tr>
                        <td>a)</td>
                        <td>y = 1 + x</td>
                        <td>1</td>
                        <td>1.000</td>
                        <td>🥈 2º</td>
                    </tr>
                    <tr>
                        <td>b)</td>
                        <td>y = -2 + 2x</td>
                        <td>4</td>
                        <td>4.000</td>
                        <td>🥉 3º</td>
                    </tr>
                </tbody>
            </table>
        </div>

        <div class="result-highlight">
            🏆 GANADORA: Opción c) y = 2/3 + x<br>
            Con el menor error cuadrático: SSE = 2/3 ≈ 0.667
        </div>

        <div class="section">
            <h2>📊 Gráfico Comparativo</h2>
            <div class="chart-container">
                <canvas id="comparisonChart"></canvas>
            </div>
        </div>

        <div class="section">
            <h2>🔍 Análisis Matemático Detallado</h2>
            <div style="background: #f8f9fa; padding: 20px; border-radius: 10px; margin: 20px 0;">
                <h4>📐 Cálculo Exacto con Fracciones:</h4>
                <p><strong>Opción c) y = 2/3 + x:</strong></p>
                <ul>
                    <li>Punto (1,2): Error = 2 - (2/3 + 1) = 2 - 5/3 = 6/3 - 5/3 = 1/3</li>
                    <li>Punto (2,2): Error = 2 - (2/3 + 2) = 2 - 8/3 = 6/3 - 8/3 = -2/3</li>
                    <li>Punto (3,4): Error = 4 - (2/3 + 3) = 4 - 11/3 = 12/3 - 11/3 = 1/3</li>
                </ul>
                <p><strong>SSE = (1/3)² + (-2/3)² + (1/3)² = 1/9 + 4/9 + 1/9 = 6/9 = 2/3</strong></p>
            </div>

            <div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 20px; margin: 20px 0;">
                <div style="background: #e8f5e8; padding: 15px; border-radius: 10px; text-align: center;">
                    <h4>Opción A</h4>
                    <p><strong>y = 1 + x</strong></p>
                    <p>SSE = 1</p>
                    <p>Errores: 0, -1, 0</p>
                </div>
                <div style="background: #fff5e6; padding: 15px; border-radius: 10px; text-align: center;">
                    <h4>Opción B</h4>
                    <p><strong>y = -2 + 2x</strong></p>
                    <p>SSE = 4</p>
                    <p>Errores: 2, 0, 0</p>
                </div>
                <div style="background: #e8f8e8; padding: 15px; border-radius: 10px; text-align: center; border: 3px solid #2ecc71;">
                    <h4>🏆 Opción C</h4>
                    <p><strong>y = 2/3 + x</strong></p>
                    <p>SSE = 2/3 ≈ 0.667</p>
                    <p>Errores: 1/3, -2/3, 1/3</p>
                </div>
            </div>
        </div>

        <div class="section">
            <h2>💡 Conclusión</h2>
            <p style="font-size: 1.2em; line-height: 1.6; text-align: justify;">
                La opción <strong>c) y = 2/3 + x</strong> es la ganadora porque presenta el menor error cuadrático medio (SSE = 2/3). 
                Esta recta ofrece el mejor compromiso entre todos los puntos, distribuyendo los errores de manera más equilibrada 
                que las otras opciones. Los errores son relativamente pequeños y están bien distribuidos alrededor de cero.
            </p>
        </div>
    </div>

    <script>
        // Datos para el gráfico
        const ctx = document.getElementById('comparisonChart').getContext('2d');
        
        // Datos originales
        const originalData = [
            {x: 1, y: 2},
            {x: 2, y: 2},
            {x: 3, y: 4}
        ];

        // Generar puntos para las rectas
        const xValues = [0.5, 1, 1.5, 2, 2.5, 3, 3.5];
        
        const lineA = xValues.map(x => ({x: x, y: 1 + x}));
        const lineB = xValues.map(x => ({x: x, y: -2 + 2*x}));
        const lineC = xValues.map(x => ({x: x, y: 2/3 + x}));

        new Chart(ctx, {
            type: 'scatter',
            data: {
                datasets: [
                    {
                        label: 'Datos Originales',
                        data: originalData,
                        backgroundColor: '#e74c3c',
                        borderColor: '#c0392b',
                        borderWidth: 3,
                        pointRadius: 10,
                        pointHoverRadius: 15,
                        pointStyle: 'circle'
                    },
                    {
                        label: 'c) y = 2/3 + x (SSE = 2/3 ≈ 0.667) 🏆',
                        data: lineC,
                        type: 'line',
                        fill: false,
                        borderColor: '#2ecc71',
                        backgroundColor: '#2ecc71',
                        borderWidth: 5,
                        pointRadius: 0,
                        tension: 0
                    },
                    {
                        label: 'a) y = 1 + x (SSE = 1)',
                        data: lineA,
                        type: 'line',
                        fill: false,
                        borderColor: '#3498db',
                        backgroundColor: '#3498db',
                        borderWidth: 3,
                        pointRadius: 0,
                        tension: 0
                    },
                    {
                        label: 'b) y = -2 + 2x (SSE = 4)',
                        data: lineB,
                        type: 'line',
                        fill: false,
                        borderColor: '#f39c12',
                        backgroundColor: '#f39c12',
                        borderWidth: 3,
                        pointRadius: 0,
                        tension: 0
                    }
                ]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    title: {
                        display: true,
                        text: 'Comparación de Rectas - Ganadora: y = 2/3 + x',
                        font: {
                            size: 18,
                            weight: 'bold'
                        },
                        color: '#2c3e50'
                    },
                    legend: {
                        display: true,
                        position: 'top',
                        labels: {
                            font: {
                                size: 13
                            },
                            color: '#2c3e50'
                        }
                    }
                },
                scales: {
                    x: {
                        title: {
                            display: true,
                            text: 'x',
                            font: {
                                size: 16,
                                weight: 'bold'
                            },
                            color: '#2c3e50'
                        },
                        min: 0.5,
                        max: 3.5,
                        grid: {
                            color: '#ecf0f1'
                        }
                    },
                    y: {
                        title: {
                            display: true,
                            text: 'y',
                            font: {
                                size: 16,
                                weight: 'bold'
                            },
                            color: '#2c3e50'
                        },
                        min: -1,
                        max: 5,
                        grid: {
                            color: '#ecf0f1'
                        }
                    }
                },
                interaction: {
                    intersect: false,
                    mode: 'index'
                },
                animation: {
                    duration: 2000,
                    easing: 'easeInOutQuart'
                }
            }
        });
    </script>
</body>
</html>
