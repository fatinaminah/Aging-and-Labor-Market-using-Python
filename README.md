
# Trends of Demographic Aging and Labor Market in Japan Using Python

**Falling fertility rates in East Asia**

East Asia is undergoing a significant demographic shift marked by declining birth rates and an aging population. In 2023, both South Korea and China reported total fertility rates (TFR) lower than Japan’s. The TFR, which represents the average number of children born per woman in these countries, remains below the population replacement level of 2.06, with South Korea at around 0.72, China at 0.999, and Japan at 1.208. This ongoing decline in fertility rates points to a continued acceleration of population aging. A fertility rate below the replacement level means that, over time, each new generation will be smaller than the last, leading to demographic and economic challenges.

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


**Impact of low fertility rates on ageing populations**

A lower fertility rate accelerates the aging of the population, increasing the proportion of elderly individuals. As birth rates continue to fall, the shift toward an older society becomes more noticeable. This trend is particularly prominent in high-income nations, where aging has become a defining characteristic. In 2023, Japan had nearly 30% of its population aged 65 and older, while South Korea and China had elderly population shares of approximately 18% and 14%, respectively.

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

The total dependency ratio is the sum of both. In Japan, the child dependency ratio has consistently decreased, while the aged dependency ratio has been on the rise since the mid-1990s. This ongoing increase in the overall dependency ratio is anticipated to impose growing financial and social burdens on Japan’s working population.

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


**The impacts of demographic changes on labor supply**


Demographic changes have a profound effect on a nation’s labor force. As populations age, birth rates fluctuate, and migration patterns evolve, the labor supply undergoes significant transformations, which in turn affect economic growth.

In Japan, female labor force participation has steadily risen over the years. By 2023, the participation rate reached 54.85%, an increase from 54.2% in 2022. During the same period, Japan’s nominal GDP per capita was around $49,885.20. Studies suggest that higher female labor force participation can have a positive impact on economic growth, with evidence showing that increasing the number of women in the workforce can lead to substantial GDP gains.

While a direct link between female labor force participation and GDP per capita in Japan requires further research, the growing trend of female employment mirrors global patterns where higher female participation in the workforce fosters broader economic development.

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
