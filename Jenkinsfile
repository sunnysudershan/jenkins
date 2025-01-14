pipeline {
    agent any
    environment {
        REPO_NAME = 'registry.aus.edu/demo-2/my-app'
        REGISTRY_SELECTION = 'rmt'
        CONTROLLER = 'NeuVector-Controller-1'
        MAX_CONCURRENT_SCANS = 32
    }
    stages {
        stage('Parallel Vulnerability Scanning') {
            steps {
                script {
                    // List of tags to scan
                    TAGS_LIST_PART1 = ["1.0"]
                    TAGS_LIST_PART2 = ["2.0"]
                    // Add more parts if necessary (e.g., additional tags)
                    
                    def allTags = TAGS_LIST_PART1 + TAGS_LIST_PART2
                    def batches = allTags.collate(MAX_CONCURRENT_SCANS.toInteger()) // Ensure MAX_CONCURRENT_SCANS is an integer
                    def batchCounter = 1
                    
                    for (batch in batches) {
                        stage("Batch ${batchCounter}") {
                            def scans = [:]
                            batch.each { tag ->
                                def currentTag = tag
                                scans["Scan ${currentTag}"] = {
                                    stage("Scan ${currentTag}") {
                                        neuvector(
                                            controllerEndpointUrlSelection: CONTROLLER,
                                            registrySelection: REGISTRY_SELECTION,
                                            repository: REPO_NAME,
                                            scanTimeout: 20,
                                            tag: "${currentTag}",
                                            scanLayers: true
                                        )
                                        echo "Scan for tag ${currentTag} complete"
                                    }
                                }
                            }
                            parallel scans
                        }
                        batchCounter++
                    }
                }
            }
        }
    }
}
