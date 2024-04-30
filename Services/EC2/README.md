#!/bin/bash

# Create EC2 directory
mkdir -p "Amazon Elastic Compute Cloud (EC2)"

# Change directory to EC2
cd "Amazon Elastic Compute Cloud (EC2)"

# Create Code Samples directory
mkdir -p "Code Samples"
cat <<EOF > "Code Samples/README.md"
# Code Samples

The Code Samples section is like a cookbook filled with recipes. Each recipe, or code sample, is a self-contained guide that shows you how to perform a specific task in EC2. For example, a code sample might show you how to launch an EC2 instance, how to configure an instance, or how to take snapshots of an instance for backup purposes.

These code samples are written in a variety of programming languages and use AWS SDKs. They are designed to be easy to understand and practical to use. You can copy these code samples directly into your own projects, or you can use them as a starting point for your own custom solutions.
EOF

# Create Best Practices directory
mkdir -p "Best Practices"
cat <<EOF > "Best Practices/README.md"
# Best Practices

The Best Practices section is like a mentor who shares wisdom and advice. This section contains guidelines and recommendations that can help you get the most out of EC2. These best practices cover a wide range of topics, including how to optimize performance, how to improve security, and how to save costs.

These best practices are based on the collective experience of AWS architects and engineers, industry experts, and successful customers. They are not just theoretical ideas, but practical tips that have been proven to work in real-world scenarios.
EOF

# Create Documentation directory
mkdir -p "Documentation"
cat <<EOF > "Documentation/README.md"
# Documentation

The Documentation section is like a library filled with reference books. Each document is a comprehensive guide that covers a specific topic in depth. For example, a document might provide a detailed tutorial on how to set up a web server on EC2, how to host a database on EC2, or how to use EC2 for application hosting.

These documents are written in a clear and concise style, with step-by-step instructions and helpful diagrams. They are designed to be easy to follow, even if you are new to EC2 or cloud computing in general.
EOF

echo "EC2 directory structure and README.md files created successfully!"
