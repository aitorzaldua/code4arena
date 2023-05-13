# Overview

Venus es un DeFi AMM (algorith money market) que funciona en la BNB Chain.

Los fondos de préstamos descentralizados (Decentralized Lending Pools) son muy similares a los servicios de préstamos tradicionales ofrecidos por los bancos, salvo que son ofrecidos por plataformas descentralizadas P2P, es decir, por partículares.

Los usuarios pueden apalancar activos (Leverage Assets) tomando prestados (Borrow) y prestando (Lending) activos listados en un pool. Los pools de préstamos (Lending pool) ayudan a los cripto poseedores (holders) a obtener unos ingresos sustanciales a través de los intereses pagados por sus activos suministrados y a acceder a activos que actualmente no poseen sin vender nada de su cartera (portfolio).

La primera generación de pools de préstamo (Lending Pools), incluyendo el Venus Core Pool, agrega un grupo diverso de activos para que los usuarios interactúen con ellos. Esto introduce un riesgo significativo para la liquidez de todo el protocolo (Protocol's Liquidity) si cualquier token incluido en el fondo experimenta una volatilidad extrema. Es difícil listar nuevos tokens debido a la falta de parámetros de riesgo específicos. El Venus Core Pool también carece de parámetros de análisis de riesgo para el déficit del pool (pool's shortfall), lo que daría a los usuarios una visión de la estabilidad actual del mercado.

`Venus Isolated Pools` está diseñado para abordar todas las deficiencias que tenían sus versiones anteriores. Los Isolated Pools, o Pools Aislados, se componen de conjuntos independientes de activos con configuraciones personalizadas de gestión del riesgo (Custom Risk Management Configurations), lo que ofrece a los usuarios mayores oportunidades de gestionar el riesgo, asignar sus activos en el protocolo y obtener rentabilidad (Yield). Los múltiples Isolated pools también reducen el impacto de cualquier posible fallo de los activos que afecte a la liquidez del protocolo. Las recompensas (Rewards) pueden personalizarse por mercado en cada pool para ofrecer los mejores incentivos a los usuarios.
