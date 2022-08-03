# istio-testing

## how to run istio e2e 

// create kind cluster
./prow/integ-suite-kind.sh  --skip-cleanup

export HUB=localhost:5000
export TAG=8-3

make docker

set up istio and run test case
```
go test  -tags=integ -vet=off ./tests/integration/security/... -timeout 30m  --istio.test.hub=${HUB} --istio.test.tag=${TAG} --istio.test.nocleanup \
--test.run=TestAuthz_WorkloadSelector
```
