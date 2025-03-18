from graphviz import Digraph

def create_architecture():
    dot = Digraph("Attack Detection Architecture")
    
    # Nodes
    dot.node("User", "USER", shape="oval", style="filled", fillcolor="lightblue")
    dot.node("Dataset", "DATASET", shape="box", style="filled", fillcolor="lightgrey")
    dot.node("Processing", "PROCESSING", shape="box", style="filled", fillcolor="lightyellow")
    dot.node("AlgorithmSelection", "ALGORITHM SELECTION", shape="box", style="filled", fillcolor="lightgreen")
    dot.node("Prediction", "PREDICTION", shape="box", style="filled", fillcolor="lightcoral")
    
    # Algorithms
    dot.node("LSTM", "LSTM", shape="ellipse", style="filled", fillcolor="lightpink")
    dot.node("CNN", "CNN", shape="ellipse", style="filled", fillcolor="lightpink")
    dot.node("RNN", "RNN", shape="ellipse", style="filled", fillcolor="lightpink")
    dot.node("ANN", "ANN", shape="ellipse", style="filled", fillcolor="lightpink")
    dot.node("RandomForest", "Random Forest", shape="ellipse", style="filled", fillcolor="lightpink")
    
    # Attack Types
    dot.node("Normal", "NORMAL", shape="ellipse", style="filled", fillcolor="lightgrey")
    dot.node("Neptune", "NEPTUNE", shape="ellipse", style="filled", fillcolor="red")
    dot.node("Warezclient", "WAREZCLIENT", shape="ellipse", style="filled", fillcolor="red")
    dot.node("IPsweep", "IPSWEEP", shape="ellipse", style="filled", fillcolor="red")
    dot.node("Portsweep", "PORTSWEEP", shape="ellipse", style="filled", fillcolor="red")
    dot.node("Teardrop", "TEARDROP", shape="ellipse", style="filled", fillcolor="red")
    dot.node("Etc", "ETC", shape="ellipse", style="filled", fillcolor="red")
    
    # Connections
    dot.edge("User", "Dataset")
    dot.edge("Dataset", "Processing")
    dot.edge("Processing", "AlgorithmSelection")
    
    # Connecting Algorithms
    dot.edge("AlgorithmSelection", "LSTM")
    dot.edge("AlgorithmSelection", "CNN")
    dot.edge("AlgorithmSelection", "RNN")
    dot.edge("AlgorithmSelection", "ANN")
    dot.edge("AlgorithmSelection", "RandomForest")
    
    # Connecting to Prediction
    dot.edge("LSTM", "Prediction")
    dot.edge("CNN", "Prediction")
    dot.edge("RNN", "Prediction")
    dot.edge("ANN", "Prediction")
    dot.edge("RandomForest", "Prediction")
    
    # Prediction to Attack Types
    dot.edge("Prediction", "Normal")
    dot.edge("Prediction", "Neptune")
    dot.edge("Prediction", "Warezclient")
    dot.edge("Prediction", "IPsweep")
    dot.edge("Prediction", "Portsweep")
    dot.edge("Prediction", "Teardrop")
    dot.edge("Prediction", "Worms")
    
    return dot

# Generate and render the architecture
architecture = create_architecture()
architecture.render("attack_detection_architecture", format="png", cleanup=False)
