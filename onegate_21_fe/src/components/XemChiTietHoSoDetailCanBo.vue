<template>
  <div class="form-chitiet">
    <content-placeholders class="mt-3" v-if="loading">
      <content-placeholders-text :lines="1" />
    </content-placeholders>
    <div v-else class="row-header" style="margin-top: 6px;">
      <div class="background-triangle-big"> <span>CHI TIẾT HỒ SƠ</span> </div>
      <div class="layout row wrap header_tools row-blue">
        <div class="flex xs8 sm10 pl-3 text-ellipsis text-bold" :title="thongTinChiTietHoSo.serviceName">
          {{thongTinChiTietHoSo.serviceName}}
        </div>
        <div class="flex xs4 sm2 text-right" style="margin-left: auto;">
          <v-btn flat class="my-0 mx-0 btn-border-left" @click="goBack" active-class="temp_active">
            Quay lại &nbsp;
            <v-icon size="16">undo</v-icon>
          </v-btn>
        </div>
      </div> 
    </div>
    <v-expansion-panel class="expansion-pl">
      <v-expansion-panel-content hide-actions value="1">
        <div slot="header"><div class="background-triangle-small"> <v-icon size="18" color="white">star_rate</v-icon> </div>THÔNG TIN CHUNG HỒ SƠ</div>
        <v-card>
          <v-card-text>
            <v-layout wrap>
              <v-flex xs12 sm2>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0">Tên doanh nghiệp: </v-subheader>
              </v-flex>
              <v-flex xs12 sm4>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0 header-text-field"> {{thongTinChiTietHoSo.applicantName}}</v-subheader>
              </v-flex>
              <!--  -->
              <v-flex xs12 sm2>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0">Thời gian gửi: </v-subheader>
              </v-flex>
              <v-flex xs12 sm4>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0 header-text-field"> {{thongTinChiTietHoSo.submitDate}} </v-subheader>
              </v-flex>
              <!--  -->
              <v-flex xs12 sm2>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0">Mã hồ sơ: </v-subheader>
              </v-flex>
              <v-flex xs12 sm4>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0 header-text-field">  {{thongTinChiTietHoSo.dossierIdCTN}} </v-subheader>
              </v-flex>
              <!--  -->
              <v-flex xs12 sm2>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0">Thời gian tiếp nhận: </v-subheader>
              </v-flex>
              <v-flex xs12 sm4>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0 header-text-field"> {{thongTinChiTietHoSo.receiveDate}}</v-subheader>
              </v-flex>
              <!--  -->
              <v-flex xs12 sm2>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0">Số hồ sơ: </v-subheader>
              </v-flex>
              <v-flex xs12 sm4>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0 header-text-field"> {{thongTinChiTietHoSo.dossierNo}} </v-subheader>
              </v-flex>
              <!--  -->
              <v-flex xs12 sm2>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0">Thời hạn xử lý: </v-subheader>
              </v-flex>
              <v-flex xs12 sm4>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0 header-text-field"> <i>{{thongTinChiTietHoSo.durationDate}} làm việc</i> </v-subheader>
              </v-flex>
              <v-flex xs12 sm2>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader :title="!showContactDetail?'Chi tiết liên hệ':'Thu gọn'" v-else class="pl-0 hover-pointer" @click.prevent.stop="showContactDetail = !showContactDetail">
                  Thông tin liên hệ:
                </v-subheader>
              </v-flex>
              <v-flex xs12 sm4>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0 header-text-field hover-pointer"> 
                  <span :title="!showContactDetail?'Chi tiết liên hệ':'Thu gọn'" @click.prevent.stop="showContactDetail = !showContactDetail">
                    <v-icon color="primary" v-if="!showContactDetail">keyboard_arrow_down</v-icon>
                    <v-icon color="primary" v-if="showContactDetail">keyboard_arrow_up</v-icon>
                  </span>
                </v-subheader>
              </v-flex>
              <!--  -->
              <v-flex xs12 sm2>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0">Trạng thái: </v-subheader>
              </v-flex>
              <v-flex xs12 sm4>
                <content-placeholders class="mt-1" v-if="loading">
                  <content-placeholders-text :lines="1" />
                </content-placeholders>
                <v-subheader v-else class="pl-0 header-text-field"> {{thongTinChiTietHoSo.dossierStatusText}} </v-subheader>
              </v-flex>
              <v-flex xs12 sm12>
                <v-slide-y-transition>
                  <div v-if="showContactDetail">
                    <v-layout wrap>
                      <v-flex xs12 sm2>
                        <v-subheader class="pl-0"><i>Tên doanh nghiệp: </i></v-subheader>
                      </v-flex>
                      <v-flex xs12 sm4>
                        <v-subheader class="pl-0 header-text-field"> {{thongTinChiTietHoSo.applicantName}} </v-subheader>
                      </v-flex>
                      <v-flex xs12 sm2>
                        <v-subheader class="pl-0"><i>Địa chỉ Email: </i></v-subheader>
                      </v-flex>
                      <v-flex xs12 sm4>
                        <v-subheader class="pl-0 header-text-field"> {{thongTinChiTietHoSo.contactEmail}} </v-subheader>
                      </v-flex>
                      <v-flex xs12 sm2>
                        <v-subheader class="pl-0"><i>Số điện thoại: </i></v-subheader>
                      </v-flex>
                      <v-flex xs12 sm4>
                        <v-subheader class="pl-0 header-text-field"> {{thongTinChiTietHoSo.contactTelNo}} </v-subheader>
                      </v-flex>
                      <v-flex xs12 sm2>
                        <v-subheader class="pl-0"><i>Địa chỉ: </i></v-subheader>
                      </v-flex>
                      <v-flex xs12 sm4>
                        <v-subheader class="pl-0 header-text-field"> {{thongTinChiTietHoSo.address}} </v-subheader>
                      </v-flex>
                    </v-layout>
                  </div>
                </v-slide-y-transition>
              </v-flex>
              
            </v-layout>
          </v-card-text>
        </v-card>
      </v-expansion-panel-content>
    </v-expansion-panel>
    <!--  -->
    <div>
      <v-tabs slider-color="primary" style="background-color: #dae8e8;" reverse-transition="fade-transition" transition="fade-transition">
        <v-tab key="1" class="mr-2">
          THÀNH PHẦN HỒ SƠ
        </v-tab>
        <v-tab key="2" class="mr-2" @click="getNextActions()">
          THỤ LÝ HỒ SƠ
        </v-tab>
        <v-tab key="3" class="mr-2" @click="loadDossierActions()">
          TIẾN TRÌNH THỤ LÝ
        </v-tab>
        <v-tab key="4" class="mr-2" @click="loadDossierLogs()">
          NHẬT KÝ HỒ SƠ
        </v-tab>
        <v-tab key="5">
          TRAO ĐỔI THẢO LUẬN
        </v-tab>
        <v-tab key="6" @click="loadDossierSyncs()">
          TRAO ĐỔI NỘI BỘ
        </v-tab>
        <!--  -->
        <v-tab-item key="1">
          <v-expansion-panel expand class="my-0 expansion-pl-transparent" style="border: none">
            <v-expansion-panel-content v-bind:value="true">
              <div slot="header" class="text-bold">
                <div class="background-triangle-small"> I.</div>
                Tài liệu nộp
              </div>
              <div v-for="(item, index) in dossierTemplatesTN" v-bind:key="item.partNo">
                <v-card>
                  <v-layout wrap class="px-3 py-1 align-center row-list-style" style="border-bottom: 1px solid #ddd"> 
                    <v-flex xs11>
                      <span class="text-bold" style="position: absolute;">{{index + 1}}.</span> 
                      <div style="margin-left: 30px;">{{item.partName}}</div>
                    </v-flex>
                    <v-flex xs1 class="text-right">
                      <v-tooltip top>
                        <v-btn slot="activator" class="mx-0 my-0" fab dark small color="primary" @click="viewFile(item)" style="height:25px;width:25px">
                          {{item.count}}
                        </v-btn>
                        <span>Xem</span>
                      </v-tooltip>
                    </v-flex>
                  </v-layout>
                </v-card>
              </div>
            </v-expansion-panel-content>
          </v-expansion-panel>
          <v-expansion-panel expand class="my-0 expansion-pl-transparent" style="border: none">
            <v-expansion-panel-content v-bind:value="true">
              <div slot="header" class="text-bold">
                <div class="background-triangle-small"> II.</div>
                Kết quả
              </div>
              <div v-for="(item, index) in dossierTemplatesKQ" v-bind:key="item.partNo">
                <v-card>
                  <v-layout wrap class="px-3 py-1 align-center row-list-style" style="border-bottom: 1px solid #ddd"> 
                    <v-flex xs11>
                      <span class="text-bold" style="position: absolute;">{{index + 1}}.</span> 
                      <div style="margin-left: 30px;">{{item.partName}}</div>
                    </v-flex>
                    <v-flex xs1 class="text-right">
                      <v-tooltip top>
                        <v-btn slot="activator" class="mx-0 my-0" fab dark small color="primary" @click="viewFile(item)" style="height:25px;width:25px">
                          {{item.count}}
                        </v-btn>
                        <span>Xem</span>
                      </v-tooltip>
                    </v-flex>
                  </v-layout>
                </v-card>
              </div>
            </v-expansion-panel-content>
          </v-expansion-panel>
          <v-expansion-panel expand class="my-0 expansion-pl-transparent" style="border: none">
            <v-expansion-panel-content v-bind:value="true">
              <div slot="header" class="text-bold">
                <div class="background-triangle-small"> III.</div>
                Văn bản hành chính
              </div>
              <div v-for="(item, index) in documents" v-bind:key="item.documentCode">
                <v-card>
                  <v-layout wrap class="px-3 py-1 align-center row-list-style" style="border-bottom: 1px solid #ddd"> 
                    <v-flex xs11>
                      <span class="text-bold" style="position: absolute;">{{index + 1}}.</span> 
                      <div style="margin-left: 30px;">{{item.documentName}}</div>
                    </v-flex>
                    <v-flex xs1 class="text-right">
                      <v-tooltip top>
                        <v-btn slot="activator" class="mx-0 my-0" fab dark small color="primary" @click="viewFile(item)" style="height:25px;width:25px">
                          <v-icon>visibility</v-icon>
                        </v-btn>
                        <span>Xem</span>
                      </v-tooltip>
                    </v-flex>
                  </v-layout>
                </v-card>
              </div>
            </v-expansion-panel-content>
          </v-expansion-panel>
          <!-- <v-expansion-panel expand class="my-0 expansion-pl-transparent" style="border: none">
            <v-expansion-panel-content v-bind:value="true">
              <div slot="header" class="text-bold">
                <div class="background-triangle-small"> IV.</div>
                Chứng từ thanh toán
              </div>
              <div v-for="(item, index) in payments" :key="item.referenceUid">
                <v-card>
                  <v-layout wrap class="px-3 py-1 align-center row-list-style" style="border-bottom: 1px solid #ddd"> 
                    <v-flex xs11>
                      <span class="text-bold" style="position: absolute;">{{index + 1}}.</span> 
                      <div style="margin-left: 30px;">{{item.paymentFee}}</div>
                    </v-flex>
                    <v-flex xs1 class="text-right">
                      <v-tooltip top>
                        <v-btn slot="activator" class="mx-0 my-0" fab dark small color="primary" @click="viewFile(item)" style="height:25px;width:25px">
                          <v-icon>visibility</v-icon>
                        </v-btn>
                        <span>Xem</span>
                      </v-tooltip>
                    </v-flex>
                  </v-layout>
                </v-card>
              </div>
            </v-expansion-panel-content>
          </v-expansion-panel> -->
        </v-tab-item>
        <v-tab-item key="2" style="background: #ffff;">
          <v-btn color="primary" v-for="(item, index) in nextActions" @click="getNextAction(item)" :key="item.processActionId">{{item.actionName}}</v-btn>
          <v-card v-if="stepModel != null">
            <div v-if="stepModel.plugin">
              <div v-if="stepModel.pdf">
                <div class="flex xs12 sm12 text-center">
                  <object id="dossierPDFViewPlugin" data="" width="100%" height="100%">
                    <iframe :src="stepModel.url" width="100%" height="100%"> </iframe>
                  </object>
                  <div id="dossierPDFViewNotFound" class="text-center">{{ stepModel.no_pdf }}</div>
                </div>
              </div>

              <div v-if="stepModel.html">
                <input type="hidden" class="dossierFilePartNo" name="">
                <div id="alpacajs_form_plugin" class="expansion-panel__header"></div>
                <div id="dossierAlpacaNotFound" class="text-center">{{ stepModel.no_html }}</div>
              </div> 
            </div>
            <div v-else>
              <v-card-title primary-title class="mx-2 pb-0" v-if="stepModel.createFiles">
                <v-layout wrap> 
                  <v-flex xs12 id="labelTPKQ" class="text-bold">
                    File đính kèm:
                  </v-flex>
                </v-layout>
              </v-card-title>
              <v-expansion-panel class="my-0 expansion__list_style">
                <v-expansion-panel-content v-for="(item,i) in stepModel.createFiles" v-if="item" :key="item.dossierPartId" class="pl-3 pr-3">
                  <div slot="header" @click.prevent="showAlpacaJSFORM(item)">{{i + 1}}. {{item.partName}} <small v-if="item.eform">( <i style="color: blue;">Form trực tuyến</i> )</small> </div>
                  <div slot="header" class="text-right">
                    <v-btn flat icon light class="small-btn-x mx-0 my-0" v-on:click.native.prevent="pickFile(item)">
                      <v-icon>file_upload</v-icon>
                    </v-btn>
                    <v-btn color="primary" fab small dark class="small-btn-x mx-0 my-0" v-on:click.native.prevent="viewDossierFileResult(item, i)" :id="'btn-count-partno'+item.partNo">
                      <!-- {{item.counter}} --> 0
                    </v-btn>
                    <v-btn flat icon light class="small-btn-x mx-0 my-0" v-on:click.native.prevent="deleteDossierFileVersion(item)">
                      <v-icon>delete</v-icon>
                    </v-btn>
                  </div>
                  <input type="file" :id="'file' + item.partNo" style="display:none" v-on:change="onUploadSingleFile($event, item, i)"/>
                  <div class="text-right pr-4" v-if="item.eform">
                    <v-btn color="primary" :id="'btn-save-formalpaca'+item.partNo"
                    :referenceUid="item.referenceUid"
                    :dossierId="thongTinChiTietHoSo.dossierId"
                    class="saveForm"
                    :loading="loadingAlpacajsForm"
                    :disabled="loadingAlpacajsForm"
                    v-on:click.native.prevent.stop="submitAlpacajsForm(item)"> Ghi lại </v-btn>
                  </div>
                  <div :id="'formAlpaca' + item.partNo" class="expansion-panel__header"></div>
                  <input type="hidden" :id="'dossierFileId' + item.partNo" :value="item.dossierFileId" />
                </v-expansion-panel-content>
              </v-expansion-panel>
              <v-card-title primary-title class="mx-2 py-0">
                <v-layout wrap> 
                  <v-flex xs12 v-if="stepModel.allowAssignUser > 0" class="mt-2 text-bold">
                    Phân công:
                  </v-flex>
                  <v-flex xs12 class="mb-3" v-if="stepModel.allowAssignUser > 0">
                    <phancong v-model="stepModel.toUsers" :type="stepModel.allowAssignUser"></phancong> 
                  </v-flex>
                  <v-flex xs12>
                    Nhập ý kiến {{stepModel.actionName}}:
                    <v-text-field
                    v-model="actionNote"
                    multi-line
                    ></v-text-field>
                  </v-flex>
                </v-layout>
              </v-card-title>
              <v-card-actions>
                <v-btn flat color="primary" class="px-0" :loading="actionsSubmitLoading" :disabled="actionsSubmitLoading"
                @click.prevent.stop="postNextActions(stepModel)">Xác nhận</v-btn>
              </v-card-actions>
            </div>
          </v-card>
        </v-tab-item>
        <v-tab-item key="3" style="background: #ffff;">
          <div>
            <v-data-table :headers="headers" :items="dossierActions" class="table-landing table-bordered"
            hide-actions no-data-text="Không có dữ liệu"
            >
            <template slot="headerCell" slot-scope="props">
              <v-tooltip bottom>
                <span slot="activator">
                  {{ props.header.text }}
                </span>
                <span>
                  {{ props.header.text }}
                </span>
              </v-tooltip>
            </template>
            <template slot="items" slot-scope="props">
              <td class="text-xs-center">{{props.item.sequenceRole}}</td>
              <td class="text-xs-center">{{props.item.sequenceName}}</td>
              <td class="text-xs-center">{{props.item.durationCount}} ngày</td>
              <td class="text-xs-center">{{props.item.startDate}}</td>
              <td class="text-xs-center">
                <div v-for="itemUser in props.item.assignUsers" :key="itemUser.userId">
                  {{itemUser.userName}} <br>
                </div>
              </td>
              <td>
                <div v-for="(itemAction, index) in props.item.actions" :key="index">
                  {{itemAction.actionName}} : ({{itemAction.createDate}})
                  <div v-if="index === props.item.actions.length - 1">
                    <span v-if="itemAction.actionOverdue > 0" style="color: red">Quá hạn {{itemAction.actionOverdue}} ngày</span>
                    <span v-else-if="itemAction.state === 0" style="color: blue">Đang chờ thực hiện</span>
                    <span v-else-if="itemAction.state === 1" style="color: blue">Đã thực hiện</span>
                    <span v-else style="color: blue">Quay lại bước trước</span>
                  </div>
                </div>
               <!--  <span v-if="getMaxDueDate(props.item.actions) > 0" style="color: red">Quá hạn {{props.item.actions|getMaxDueDate}} ngày</span>
                <span v-else style="color: blue">Đang thực hiện</span> -->
              </td>
            </template>
          </v-data-table>
        </div>
      </v-tab-item>
      <v-tab-item key="4" style="background: #ffff;">
        <div v-for="(item, index) in listHistoryProcessing" v-bind:key="item.dossierLogId" class="list_history_style">
          <td class="px-2 pt-2" :class="index % 2 !== 0 ? 'col-tien-trinh-1' : 'col-tien-trinh-2'">{{ index + 1 }}</td>
          <td class="text-xs-left px-2 py-2">
            <p class="mb-2"> Ông/bà <b>{{ item.author }}</b> 
              <span style="color: #0b72ba">( {{ item.payload.stepName }} )</span>
              <br/>
              <span style="color: #939393">{{ item.createDate | dateTimeView }}</span>
            </p>
            Ý kiến: <span v-html="item.content"></span> <br>
            <p
            class="history__download__link hover-pointer-download"
            title="Tải file"
            v-for="file in item.payload.files"
            :key="file.dossierFileId"
            @click.prevent.stop="downloadFileLogs(file.dossierFileId)"
            >
            <v-icon>file_download</v-icon> 
            <span>{{file.fileName}}</span>
          </p>
        </td>
      </div>
    </v-tab-item>
    <v-tab-item key="5" style="background: #ffff;">
      <comment :classPK="dossierId" :className="className"></comment>
    </v-tab-item>
    <v-tab-item key="6" style="background: #ffff;">
      <v-layout row wrap>
        <v-flex xs12 sm3>
        </v-flex>
        <v-flex xs12 sm6>
          <v-card>
            <div style="height: 400px; overflow: auto; margin-bottom: 10px;">
              <div v-for="(item, index) in dossierSyncs" v-bind:key="index">
                <div :class="{ 'text-xs-left': item.syncType === 1, 'text-xs-right': item.syncType === 2 }">
                  <v-chip label :color="getColorChat(item.syncType)" text-color="white">
                    {{item.actionUser}}: {{item.actionNote}}
                  </v-chip>
                </div>
              </div>
            </div>
            <v-text-field
            v-model="messageChat"
            solo
            label="Nhập trao đổi"
            append-icon="send"
            @change="postChat"
            ></v-text-field>
          </v-card>
        </v-flex>
        <v-flex xs12 sm3>
        </v-flex>
      </v-layout>
    </v-tab-item>
  </v-tabs>
</div>
  </div>
</template>

<script>
import $ from 'jquery'
import '../store/jquery_comment'
import Comment from './Comment.vue'
import PhanCong from './form_xu_ly/PhanCongNguoiThucHien.vue'
export default {
  props: ['index', 'id'],
  components: {
    'comment': Comment,
    'phancong': Phancong
  },
  data: () => ({
    dossierId: '',
    className: 'org.opencps.dossiermgt.model.Dossier',
    dossierFilesItems: [],
    dossierTemplatesItems: [],
    showContactDetail: false,
    listHistoryProcessing: [],
    dossierTemplatesTN: [],
    dossierTemplatesKQ: [],
    thongTinChiTietHoSo: {
    },
    loadingAlpacajsForm: false,
    nextActions: [],
    processSteps: [],
    documents: [],
    payments: [],
    dossierActions: [],
    itemselect: '',
    dossierSyncs: [],
    stepModel: null,
    actionNote: '',
    actionsSubmitLoading: false,
    headers: [{
      text: 'Vai trò',
      align: 'center',
      sortable: false,
      class: 'vaitro_column'
    }, {
      text: 'Công việc',
      align: 'center',
      sortable: false,
      class: 'congviec_column'
    }, {
      text: 'Thời hạn quy định',
      align: 'center',
      sortable: false,
      class: 'thoihanquydinh_column'
    }, {
      text: 'Ngày bắt đầu',
      align: 'center',
      sortable: false,
      class: 'ngaybatdau_column'
    }, {
      text: 'Người thực hiện',
      align: 'center',
      sortable: false,
      class: 'nguoithuchien_column'
    }, {
      text: 'Kết quả',
      align: 'center',
      sortable: false,
      class: 'ketqua_column'
    }],
    headerSyncs: [{
      text: 'Nhật kí hồ sơ',
      align: 'center',
      sortable: false,
      class: 'nhatki_column'
    }, {
      text: 'Trao đổi trực tuyến',
      align: 'center',
      sortable: false,
      class: 'traodoitructuyen_column'
    }],
    filterDossierActionItems: [{
      text: 'Tất cả',
      value: ''
    }, {
      text: 'Có thao tác thực hiện',
      value: '1'
    }, {
      text: 'Không thao tác thực hiện',
      value: '2'
    }],
    filterDossierAction: null,
    filterDossierSyncItems: [{
      text: 'Tất cả',
      value: '1,2'
    }, {
      text: 'Thông tin trao đổi',
      value: '2'
    }],
    filterDossierSync: null,
    messageChat: ''
  }),
  computed: {
    loading () {
      return this.$store.getters.loading
    }
  },
  watch: {},
  created () {
    var vm = this
    vm.$nextTick(function () {
      vm.initData(vm.id)
    })
  },
  methods: {
    initData (data) {
      var vm = this
      vm.dossierId = data
      console.log(data)
      vm.$store.dispatch('getDetailDossier', data).then(resultDossier => {
        vm.thongTinChiTietHoSo = resultDossier
        var arrTemp = []
        console.log(resultDossier.dossierId)
        arrTemp.push(vm.$store.dispatch('loadDossierTemplates', resultDossier))
        arrTemp.push(vm.$store.dispatch('loadDossierFiles', resultDossier.dossierId))
        vm.thongTinHoSo = resultDossier
        Promise.all(arrTemp).then(values => {
          console.log(values)
          let dossierTemplates = values[0]
          let dossierFiles = values[1]
          dossierTemplates.forEach(item => {
            if (item.partType === 1) {
              vm.dossierTemplatesTN.push(item)
            } else {
              vm.dossierTemplatesKQ.push(item)
            }
          })
          vm.dossierFilesItems = dossierFiles
          vm.dossierTemplatesItems = dossierTemplates
          vm.recountFileTemplates()
        }).catch(reject => {
        })
        vm.$store.dispatch('loadDossierDocuments', resultDossier).then(resultDocuments => {
          vm.documents = resultDocuments
        })
        vm.$store.dispatch('loadDossierPayments', resultDossier).then(resultPayments => {
          vm.payments = resultPayments
        })
      })
    },
    recountFileTemplates () {
      var vm = this
      vm.dossierTemplatesItems.forEach(itemTemplate => {
        itemTemplate.count = 0
        vm.dossierFilesItems.forEach(itemFile => {
          if (itemTemplate.partNo === itemFile.dossierPartNo) {
            itemTemplate.count ++
          }
        })
      })
    },
    goBack () {
      window.history.back()
    },
    viewFile (data) {
      var vm = this
      vm.dossierFilesItems.forEach(val => {
        val['dossierId'] = vm.thongTinChiTietHoSo.dossierId
        if (val.dossierPartNo === data.partNo) {
          this.$store.dispatch('viewFile', val)
        }
      })
    },
    downloadFileLogs (data) {
      var vm = this
      let dataCommit = {
        fileAttachId: data,
        dossierId: vm.id
      }
      this.$store.dispatch('downloadFile', dataCommit)
    },
    loadDossierActions (data) {
      var vm = this
      if (vm.thongTinChiTietHoSo.dossierId) {
        let dataParams = {
          dossierId: vm.thongTinChiTietHoSo.dossierId,
          stepType: data
        }
        vm.$store.dispatch('loadDossierActions', dataParams).then(resultActions => {
          vm.dossierActions = resultActions.data
        })
      }
    },
    loadDossierSyncs (data) {
      var vm = this
      if (vm.thongTinChiTietHoSo.dossierId) {
        let dataParams = {
          dossierId: vm.thongTinChiTietHoSo.dossierId,
          info: '1,2'
        }
        vm.$store.dispatch('loadDossierSyncs', dataParams).then(resultSyncs => {
          console.log('resultSyncs++++++++++++++++', resultSyncs)
          vm.dossierSyncs = resultSyncs
        })
      }
    },
    loadDossierLogs (data) {
      var vm = this
      // data.dossierId = vm.thongTinChiTietHoSo.dossierId
      let dataParams = {
        dossierId: vm.thongTinChiTietHoSo.dossierId
      }
      let promiseHisProcessing = vm.$store.dispatch('getListHistoryProcessingItems', dataParams)
      promiseHisProcessing.then(function (result) {
        vm.listHistoryProcessing = []
        vm.listHistoryProcessing = result
      })
    },
    deleteDossierFileVersion (item) {
      var vm = this
      item['dossierId'] = vm.thongTinChiTietHoSo.dossierId
      vm.$store.dispatch('deleteAttackFiles', item).then(res => {
      })
    },
    pickFile (item) {
      document.getElementById('file' + item.partNo).click()
    },
    postChat () {
      var vm = this
      let params = {
        dossierId: vm.thongTinChiTietHoSo.dossierId,
        actionCode: 8200,
        actionNote: vm.messageChat,
        actionUser: ''
      }
      vm.$store.dispatch('postAction', params).then(result => {
        vm.loadDossierSyncs()
      })
      vm.messageChat = ''
    },
    getNextAction (item) {
      var vm = this
      if (item.type === 1) {
        let filter = {
          dossierId: vm.thongTinChiTietHoSo.dossierId,
          actionId: item.processActionId
        }
        vm.$store.dispatch('getNextAction', filter).then(resultAction => {
          vm.stepModel = resultAction
        }).catch(reject => {
          vm.stepModel = null
        })
      } else {
        let filter = {
          dossierId: vm.thongTinChiTietHoSo.dossierId,
          actionId: item.processActionId
        }
        vm.$store.dispatch('loadPlugin', filter).then(resultPlugin => {
          console.log('resultPlugin+++++++++', resultPlugin)
          vm.stepModel = resultPlugin
        }).catch(reject => {
          vm.stepModel = null
        })
      }
    },
    getNextActions () {
      var vm = this
      let params = {
        dossierId: vm.thongTinChiTietHoSo.dossierId
      }
      vm.$store.dispatch('loadProcessStep', params).then(resultNextActions => {
        console.log('resultNextActions++++++++++++', resultNextActions)
        vm.nextActions = resultNextActions
      })
    },
    showAlpacaJSFORM (item) {
      var vm = this
      if (item.eform) {
        vm.$store.dispatch('loadFormScript', item).then(resScript => {
          vm.$store.dispatch('loadFormData', item).then(resData => {
            var formScript, formData
            /* eslint-disable */
            if (resScript) {
              formScript = eval('(' + resScript + ')')
            } else {
              formScript = {}
            }
            if (resData) {
              formData = eval('(' + resData + ')')
            } else {
              formData = {}
            }
            /* eslint-disable */
            formScript.data = formData
            $('#formAlpaca' + item.partNo).alpaca(formScript)
          })
        })
      }
    },
    onUploadSingleFile (e, data, i) {
      var vm = this
      e.dataItem = data
      e['dossierId'] = vm.thongTinChiTietHoSo.dossierId
      e['dossierTemplateNo'] = vm.thongTinChiTietHoSo.dossierTemplateNo
      vm.$store.dispatch('uploadSingleFile', e).then(function (result) {
      }).catch(function (xhr) {
      })
    },
    submitAlpacajsForm (item) {
      var vm = this
      let value = {
        dossierId: vm.thongTinChiTietHoSo.dossierId,
        dossierPartNo: item.partNo
      }
      vm.$store.dispatch('putAlpacaForm', value)
    },
    getColorChat (syncType) {
      if (syncType === 1) {
        return 'pink'
      } else {
        return 'cyan lighten-1'
      }
    },
    postNextActions (stepModel) {
      var vm = this
      stepModel['dossierId'] = vm.thongTinChiTietHoSo.dossierId
      if (stepModel.allowAssignUser > 0) {
        vm.$store.dispatch('reassignDossier', stepModel).then(resReassign => {
          console.log(resReassign)
          let params = {
            dossierId: vm.dossierId,
            actionCode: stepModel.actionCode,
            actionNote: vm.actionNote,
            actionUser: '',
            payload: '',
            security: '',
            assignUsers: '',
            payment: '',
            createDossiers: ''
          }
          vm.$store.dispatch('postAction', params).then(resPostAction => {
            console.log(resPostAction)
          })
        })
      } else {
        let params = {
          dossierId: vm.dossierId,
          actionCode: stepModel.actionCode,
          actionNote: vm.actionNote,
          actionUser: '',
          payload: '',
          security: '',
          assignUsers: '',
          payment: '',
          createDossiers: ''
        }
        vm.$store.dispatch('postAction', params).then(resPostAction => {
          console.log(resPostAction)
        })
      }
    }
  },
  filters: {
    dateTimeView (arg) {
      if (arg) {
        let value = new Date(arg)
        return `${value.getDate().toString().padStart(2, '0')}/${(value.getMonth() + 1).toString().padStart(2, '0')}/${value.getFullYear()} | ${value.getHours().toString().padStart(2, '0')}:${value.getMinutes().toString().padStart(2, '0')}`
      } else {
        return ''
      }
    },
    getMaxDueDate (arr) {
      let maxDue = Math.max.apply(Math, arr.map(function (item) {
        return item.actionOverdue
      }))
      return maxDue
    }
  }
}
</script>
