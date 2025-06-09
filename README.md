# simulador
#Simulador de Autômatos com Grafos

import graphviz

dot = graphviz.Digraph(format='png')

states = ['q0', 'q1', 'q2']
final_states = ['q2']
initial_state = 'q0'

dot.attr(rankdir='LR')

dot.node('', shape='none')
dot.edge('', initial_state)

for state in states:
    shape = 'doublecircle' if state in final_states else 'circle'
    dot.node(state, shape=shape)

transitions = {
    'q0': {'0': 'q1', '1': 'q0'},
    'q1': {'0': 'q1', '1': 'q2'},
    'q2': {'0': 'q1', '1': 'q0'}
}

for from_state, paths in transitions.items():
    for symbol, to_state in paths.items():
        dot.edge(from_state, to_state, label=symbol)

dot.render('automato_grafo_simples', cleanup=True)


