.PHONY: install

BUILDER ?= erlang_builder:centos7
OTP_SRC_DIR ?= $(PWD)/otp_src
OTP_INSTALL_DIR ?= $(PWD)/otp_install

install: $(OTP_INSTALL_DIR) $(OTP_SRC_DIR)
	docker run -ti --rm=true -e "ERL_TOP=$(OTP_SRC_DIR)" -e "LANG=C" -v $(OTP_SRC_DIR):$(OTP_SRC_DIR) -v $(OTP_INSTALL_DIR):$(OTP_INSTALL_DIR) --workdir $(OTP_SRC_DIR) erlang_builder:centos7 bash -c "./otp_build autoconf && ./configure --prefix=\"$(OTP_INSTALL_DIR)\" && make && make install"

$(OTP_INSTALL_DIR):
	mkdir -p $(OTP_INSTALL_DIR)
