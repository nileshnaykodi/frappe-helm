pipeline {
	stages { 
		stage ('deploy') {
			agent {
				kubernetes {
					yamlFile pod.yaml
				}	
			} 
			steps {
				container('helm') { 
					sh 'helm repo add frappe https://helm.erpnext.com'
					sh 'helm upgrade --create-namespace --install erpstaging --namespace erpnext frappe/erpnext --set persistence.worker.enabled=false  --set ingress.enabled=false --set mariadb.enabled=false --set redis-cache.enabled=false --set redis-queue.enabled=false --set redis-socketio=false'
				}
			}
			}
	}

 	




}
