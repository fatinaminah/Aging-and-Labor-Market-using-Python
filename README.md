
# Trends of Demographic Aging and Labor Market in Japan Using Python

**Falling Birth Rates in East Asia**

East Asia is undergoing a significant demographic shift characterized by declining birth rates and an aging population. In 2023, South Korea and China recorded total fertility rates (TFR) lower than Japan’s. The TFR, which is the average number of children born per woman for all three countries remains below the population replacement level of 2.06, with South Korea at approximately 0.72, China at 0.999, and Japan at 1.208. This persistent decline in fertility suggests that population aging will continue to accelerate. A fertility rate below the replacement level indicates that, over time, each successive generation will be smaller than the previous one, posing demographic and economic challenges.

![](https://miro.medium.com/v2/resize:fit:700/1*Vuj2-Ge8gfOnzyHz56XqSg.png)

*Developed using Python, with data sourced from  [World Bank](https://data.worldbank.org/).*

    import plotly.graph_objects as go  
      
    # Create the figure  
    fig = go.Figure()  
      
    # Line chart for China  
    fig.add_trace(go.Scatter(  
        x=df['Year'],   
        y=df['China'],   
        mode='lines',  
        line=dict(dash='solid', color='maroon', width=5),  
        name="China"  
    ))  
      
    # Line chart for Japan  
    fig.add_trace(go.Scatter(  
        x=df['Year'],   
        y=df['Japan'],    
        mode='lines',  
        line=dict(dash='solid', color='darkblue', width=5),  
        name="Japan"  
    ))  
      
    # Line chart for South Korea  
    fig.add_trace(go.Scatter(  
        x=df['Year'],   
        y=df['South Korea'],    
        mode='lines',  
        line=dict(dash='solid', color='darkorange', width=5),  
        name="South Korea"  
    ))  
      
    # Update layout 
    fig.update_layout(  
        xaxis_title='Year',  
        xaxis_title_font=dict(size=16, color='black'),  
        yaxis_title='Fertility Rate',  
        yaxis_title_font=dict(size=16, color='black'),  
        hovermode='x unified',  
        showlegend=True,  
        plot_bgcolor='white',  
        xaxis=dict(  
            showgrid=False,  
            gridwidth=1,  
            ticks='outside',  
            tickcolor='gray',  
            linecolor='gray',  
            tickfont=dict(size=12)  
        ),  
        yaxis=dict(  
            showgrid=True,  
            gridcolor='gray',  
            gridwidth=1,  
            ticks='outside',  
            linecolor='gray',  
            tickfont=dict(size=12)  
        ),  
        width=900,  
        height=600  
    )  
    fig.show()


**The Impact of Low Fertility Rates on Aging Populations**

A lower fertility rate accelerates population aging, resulting in a higher proportion of elderly individuals. As birth rates continue to decline, the demographic shift toward an aging society becomes more pronounced. This trend is particularly evident in high-income economies, where aging has become a defining characteristic. In 2023, Japan had nearly 30% of its population aged 65 and older, while South Korea and China had elderly population shares of approximately 18% and 14%, respectively.

![](https://miro.medium.com/v2/resize:fit:700/1*GTtVMMb0bgI4giATswTFSQ.png)

*Developed using Python, with data sourced from  [World Bank](https://data.worldbank.org/). The proportion of elderly individuals in the total population is rising. While China and South Korea currently have lower fertility rates than Japan, their shares of elderly populations are still relatively smaller.*

    import plotly.graph_objects as go  
    # Create the figure  
    fig = go.Figure()  
      
    # Line chart for China  
    fig.add_trace(go.Scatter(  
        x=df['Year'],   
        y=df['China'],   
        mode='lines',  
        line=dict(dash='dot', color='red', width=5),  
        name="China"  
    ))  
      
    # Line chart for Japan  
    fig.add_trace(go.Scatter(  
        x=df['Year'],   
        y=df['Japan'],    
        mode='lines',  
        line=dict(dash='solid', color='blue', width=5),  
        name="Japan"  
    ))  
      
    # Line chart for South Korea  
    fig.add_trace(go.Scatter(  
        x=df['Year'],   
        y=df['South Korea'],    
        mode='lines',  
        line=dict(dash='dash', color='black', width=5),  
        name="South Korea"  
    ))  
      
    # Update layout 
    fig.update_layout(  
        title={'text': 'Share of Population Aged 65+ in Japan, China, and South Korea',   
               'font': dict(size=20),   
               'x': 0.45,   
               'xanchor': 'center'},  
        xaxis_title='Year',  
        xaxis_title_font=dict(size=14, color='black'),  
        yaxis_title='Population Ages 65+ (% of Total Population)',  
        yaxis_title_font=dict(size=14, color='black'),  
        hovermode='x unified',  
        showlegend=True,  
        plot_bgcolor='white',  
        xaxis=dict(  
            showgrid=True,  
            gridcolor='lightgray',  
            gridwidth=1,  
            tickfont=dict(size=12)  
        ),  
        yaxis=dict(  
            showgrid=True,  
            gridcolor='lightgray',  
            gridwidth=1,  
            tickfont=dict(size=12)  
        ),  
        width=900,  
        height=600  
    )  
    fig.show()


 **Total dependency population per working-age population rises**

The decline in fertility rates and an aging population are driving a rise in Japan’s dependency ratio, which measures the proportion of dependents, those younger than 15 or older than 64, relative to the working-age population (15–64 years). A higher dependency ratio places an increasing burden on the workforce, as fewer individuals are available to support dependents. As the working-age population shrinks, labor force participation declines, impacting economic productivity.

Demographic dependency is categorized into:  
• Young dependency ratio: the number of individuals aged 0–14 relative to the working-age population.  
• Old dependency ratio: the number of individuals aged 65 and older relative to the working-age population.

The total dependency ratio is the sum of both. In Japan, the child dependency ratio has steadily declined, while the aged dependency ratio has been increasing since the mid-1990s. This continuous rise in total dependency is expected to place increasing financial and social pressures on Japan’s working population.

![](https://miro.medium.com/v2/resize:fit:700/1*GbY208OY4avEHl50X0mdEw.png)

*Developed using Python, with data sourced from  [World Bank](https://data.worldbank.org/).*

    import plotly.graph_objects as go  
    import pandas as pd  
      
    # Load data  
    df = pd.read_excel(dataset_file)  
      
    # Create figure  
    fig = go.Figure()  
      
    # Add child dependency ratio as a stacked bar  
    fig.add_trace(go.Bar(x=df['Year'], y=df['Young DR'], name='Child Dependency'))  
      
    # Add aged dependency ratio as a stacked bar  
    fig.add_trace(go.Bar(x=df['Year'], y=df['Old DR'], name='Aged Dependency'))  
      
    # Add total dependency ratio as a line chart  
    fig.add_trace(go.Scatter(  
        x=df['Year'],   
        y=df['TDR'],    
        mode='lines',  
        line=dict(color='black', width=4),  
        name="Total Dependency Ratio"  
    ))  
      
    # Update layout  
    fig.update_layout(  
        barmode='stack',    
        xaxis_title='Year',  
        yaxis_title='Dependency Ratio as a Percentage of the Working-Age Population',  
        title={'text': 'Age Dependency Ratios in Japan', 'x': 0.4, 'xanchor': 'center'},  
        width=1000,  
        height=700  
    )  
      
    # Show plot  
    fig.show()


**What Do Demographic Changes Mean for Labor Supply?**

Demographic shifts significantly impact a nation’s labor force. As a population ages, birth rates fluctuate, and migration patterns change, the labor supply also transforms, influencing economic growth.

In Japan, the female labor force participation rate has consistently increased over time. In 2023, it reached 54.85%, up from 54.2% in 2022. That same year, Japan’s nominal GDP per capita was approximately $49,885.20. Research indicates that higher female labor force participation positively influences economic growth, with studies showing that increasing women’s workforce participation can significantly boost GDP.

Although a direct correlation between female labor force participation and GDP per capita in Japan requires further analysis, the rising trend of female workforce participation aligns with global patterns where higher female employment contributes to broader economic development.

![](https://miro.medium.com/v2/resize:fit:700/1*bhJCaZdoEXEqA79MWiCt6A.png)

*Developed using Python, with data sourced from  [World Bank](https://data.worldbank.org/). The labor force participation rate (LFPR) represents the percentage of the population that is actively engaged in the labor market.*

    import plotly.express as px  
    import plotly.graph_objects as go  
    from plotly.subplots import make_subplots  
           
    # Create figure with secondary y-axis  
    fig = make_subplots(specs=[[{"secondary_y": True}]])  
      
    # Add bar chart for Female Labor Force Participation Rate (Primary Y-Axis)  
    fig.add_trace(  
        go.Bar(  
            x=df['Year'],   
            y=df['FLFP'],   
            name='Female Labor Force Participation Rate',   
            marker_color='magenta'  
        ),  
        secondary_y=False  # Assign to the primary y-axis  
    )  
      
    # Add scatter plot for Total Labor Force Participation Rate (Primary Y-Axis)  
    fig.add_trace(  
        go.Scatter(  
            x=df['Year'],   
            y=df['TLFP'],    
            mode='markers+lines',  # Dots with lines  
            marker=dict(color='maroon', size=8),    
            name="Total Labor Force Participation Rate"  
        ),  
        secondary_y=False  # Assign to the primary y-axis  
    )  
      
    # Add scatter plot for GDP per capita (Secondary Y-Axis)  
    fig.add_trace(  
        go.Scatter(  
            x=df['Year'],   
            y=df['GDPPC'],   
            mode='lines',  
            line=dict(color='blue', width=3),    
            name="GDP per capita"  
        ),  
        secondary_y=True  # Assign to the secondary y-axis  
    )  
      
    # Set layout and figure size  
    fig.update_layout(  
        title={'text': 'Economic Growth and Labor Force in Japan',   
               'font': dict(size=23),   
               'x': 0.5,  # Center title  
               'xanchor': 'center'},  # Title alignment  
        xaxis=dict(title="Year"),  
        yaxis=dict(title="Labor Participation Rate (%)"),  
        yaxis2=dict(  
            title="GDP per capita (PPP, current international $)",   
            overlaying='y',   
            side='right'  
        ),  
        width=1000,    
        height=700,  
        template="plotly_dark" 
    )  
      
    # Show the plot  
    fig.show()
