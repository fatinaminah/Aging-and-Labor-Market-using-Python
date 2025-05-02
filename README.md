
# Trends of Demographic Aging and Labor Market in Japan Using Python

**Falling fertility rates in East Asia**

There is a considerable change in the demographics of East Asia as a result of reduced birth rates and an increasing older population. In 2023, both South Korea and China had TFRs below that of Japan. The average number of children born per woman in those countries has not reached the population replacement level of less than 2.06. South Korea’s is around 0.72; Europe’s is at 0.999, while Japan’s is at 1.208. This continuing decline in fertility indicates an increasing acceleration in the aging of the population. A fertility rate below that of replacement means that with time, every next generation will have fewer people as compared to the previous one.

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

Lower fertility leads to increased population age, with a growing share of older people in society. As birth rates decline, the transition to an older society is becoming more pronounced. Such transformations are clearly seen in the developed world where age becomes one of the hallmarks of a nation. Aging Japan in 2023 would have nearly 30% of the population 65 years and older; South Korea had around 18%, while China had around 14%.

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


A rising dependency ratio, defined as the ratio between the dependents (those younger than 15 or older people aged 65+) and the working-age population (15–64 years-old) follows declining fertility rates together with the aging of the population in Japan. This puts a sizeable burden on the working population, given that very few people are left to help dependents with increasingly rising dependency ratios. As the working-age population becomes smaller, labor-force participation reduces, thus reducing economic productivity.

Demographic dependency is categorized into:  
• Young dependency ratio = Number of individuals aged 0–14 as against the working-age population.  
• Old dependency ratio = Number of individuals aged 65 and above as against the working-age population.

The total dependency ratio is simply adding the two. Within Japan, the child dependency ratio has been steadily declining, while the aged dependency ratio has seen growth since the mid-1990s. This persistent rise in the overall dependency ratio is likely to thrust increasing financial and social responsibilities onto the working populace in Japan.

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


Demographic changes directly impact a country’s labor forces. Population aging, changing birth rates, and shifting migration patterns cause big changes in the labor supply that affect economic growth.

Incrementally, the female labor force participation rate has increased over the years in Japan. It reached 54.85% in 2023 from 54.2% in 2022; meanwhile, during this entire observation period, Japan’s nominal GDP per capita was roughly $49,885.20. Evidence suggests that increased female labor force participation is directly correlated to economic growth; in fact, increasing the number of women in the workforce tends to enhance the GDP tremendously.

Direct association for the female labor force participation rate with GDP per capita in Japan may need further investigation; however, the increasing female employment trend fits a global pattern in which greater female participation in the workforce catalyzes greater economic development.

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
