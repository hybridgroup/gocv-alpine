FROM denismakogon/gocv-alpine:3.4.1-buildstagegui as build-stage-gui

RUN go get -u -d gocv.io/x/gocv
RUN cd $GOPATH/src/gocv.io/x/gocv && go build -o $GOPATH/bin/gocv-capwindow ./cmd/capwindow/main.go

FROM denismakogon/gocv-alpine:3.4.1-runtimegui

COPY --from=build-stage-gui /go/bin/gocv-capwindow /gocv-capwindow
ENTRYPOINT ["/gocv-capwindow", "0"]
