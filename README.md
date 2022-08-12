# istio-testing

## how to run istio e2e 

create kind cluster and kind registry
```
./prow/integ-suite-kind.sh  --skip-cleanup
```


export HUB=localhost:5000

export TAG=8-3

build docker images and push 

```
make docker
make docker.push
```
set up istio and run test case
```
go test -v  -tags=integ -vet=off ./tests/integration/security/... -timeout 30m  --istio.test.hub=${HUB} --istio.test.tag=${TAG} --istio.test.nocleanup \
--test.run=TestAuthz_WorkloadSelector
```
